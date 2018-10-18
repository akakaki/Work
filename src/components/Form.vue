<template>
  <main class="content">
    <div class="add">
      <h2>新增單筆：</h2>
      <div>
        <ul>
          <li>
            <input v-model="title" type="text" placeholder="名稱">
            <span></span>
          </li>
          <li>
            <input v-model="price" type="text" placeholder="單價">
            <span></span>
          </li>
          <li>
            <input v-model="num" type="text" placeholder="數量">
            <span></span>
          </li>
        </ul>
        <button @click="addBtn">新增</button>
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
              <button>刪除</button>
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
      if( this.title != '' && this.price != '' && this.num != '' ){
        this.lists.push({title:this.title, price:this.price, num:this.num})   
        this.title = '',
        this.price = '',
        this.num = ''
      }else{
        alert('請完整輸入新增資訊。')
      }
    }
  }
}
</script>