<template>
  <main class="content">
    <div class="add">
      <h2>新增單筆：</h2>
      <div>
        <ul>
          <li>
            <input v-model="title" :class="{ checkInput : this.title }" type="text" placeholder="名稱">
            <span></span>
          </li>
          <li>
            <input v-model="price" :class="{ checkInput : this.price }" type="text" placeholder="單價">
            <span></span>
          </li>
          <li>
            <input v-model="num" :class="{ checkInput : this.num }" type="text" placeholder="數量">
            <span></span>
          </li>
        </ul>
        <button @click="addBtn">新增</button>
        <span class="warn">{{warnMessage}}</span>
      </div>
    </div>
    <div class="bag">
      <h2>購物清單：</h2>
      <table>
        <tbody>
          <tr>
            <th>No.</th>
            <th>名稱</th>
            <th>單價</th>
            <th>數量</th>
            <th></th>
          </tr>
          <tr v-for="(item, index) in lists" :key="item.title">
            <td>{{index + 1}}</td>
            <td>{{item.title}}</td>
            <td>{{item.price}}</td>
            <td>{{item.num}}</td>
            <td>
              <button @click="removeBtn(index)">刪除</button>
            </td>
          </tr>
        </tbody>
      </table>
      <div class="total">總價：{{totals}}</div>
    </div>
  </main>
</template>

<script>
export default {
  name: 'buyForm',
  data(){
    return{
      title: '',
      price: '',
      num: '',
      warnMessage:'',
      lists: [
        { title: '法蘭絨格紋襯衫', price: 790, num: 1 },
        { title: '羊毛法蘭絨混紡 SLIM FIT外套', price: 3990 , num: 2 },
        { title: '毛呢外套', price: 2990, num: 1 }
      ]
    }
  },
  computed:{
    totals(){
      let listLength = this.lists.length,
          prices = 0
      for( let i = 0; i < listLength; i++ ){
        prices = prices + this.lists[i].price * this.lists[i].num
      }
      return prices
    }
  },
  methods:{
    addBtn(){
      if( this.title == '' || this.price == '' || this.num == '' || isNaN(this.price) || isNaN(this.num) ){
        this.warnMessage = '* 請完整與正確填入新增資訊。'
      }else if( !Number.isInteger(Number(this.price)) || !Number.isInteger(Number(this.num)) ){
        this.warnMessage = '* 價格或數量請輸入整數。'
      }else{
        let titleArray = [],
            priceArray = [],
            reTitle,
            rePrice,
            listsLength = this.lists.length
        
        for( let i = 0; i < listsLength; i++ ){
          titleArray.push(this.lists[i].title)
          priceArray.push(this.lists[i].price)
        }
        reTitle = titleArray.indexOf(this.title)
        rePrice = priceArray.indexOf(Number(this.price))

        if( reTitle != -1 && rePrice != -1){
          this.lists[reTitle].num = this.lists[reTitle].num + Number(this.num)  
        }else{
          this.lists.push({ title: this.title, price: Number(this.price), num: Number(this.num) })
        }

        this.title = '',
        this.price = '',
        this.num = ''
      }
    },
    removeBtn(index){
      let a = confirm("是否確定刪除？");
      if (a == true) {
        this.lists.splice(index,1)
      } 
    }
  }
}
</script>