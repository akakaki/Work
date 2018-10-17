<template>
  <div id="app">
    <main class="content">
      <div class="add">
        <h2>新增單筆：</h2>
        <div>
          <ul>
            <li>
              <input type="text" placeholder="名稱">
              <span></span>
            </li>
            <li>
              <input type="text" placeholder="單價">
              <span></span>
            </li>
            <li>
              <input type="text" placeholder="數量">
              <span></span>
            </li>
          </ul>
          <button>新增</button>
        </div>
      </div>
      <div class="bag">
        <h2>購物清單：</h2>
        <table>
          <tbody>
            <tr>
              <th>No</th>
              <th>名稱</th>
              <th>單價</th>
              <th>數量</th>
              <th></th>
            </tr>
            <tr>
              <td>1</td>
              <td>Apple IPhone 8 64G</td>
              <td>18999</td>
              <td>2</td>
              <td>
                <button>刪除</button>
              </td>
            </tr>
            <tr>
              <td>2</td>
              <td>小米行動電源2C</td>
              <td>619</td>
              <td>2</td>
              <td>
                <button>刪除</button>
              </td>
            </tr>
            <tr>
              <td>3</td>
              <td>NIKE BENASSI JDI 拖鞋</td>
              <td>499</td>
              <td>2</td>
              <td>
                <button>刪除</button>
              </td>
            </tr>
          </tbody>
        </table>
        <div class="total">總價： 99999</div>
      </div>
    </main>
  </div>
</template>

<script>

export default {
  name: 'app',
  components: {
    
  }
}
</script>