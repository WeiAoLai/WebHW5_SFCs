<template>
  <div class = "head">
    <p >物價表</p>
  </div>
  <div class="background_color">
    <!-- action="http://localhost:3000" 連接到資料庫，http://localhost:3000/api-->
    <form v-on:submit.prevent="addItem" id="prices" action="http://localhost:3000/api" method="post" >
      <fieldset class="MdFormGroup01">
        <div>
          <label for="date">日期：</label>
          <input type="text" id="date" name="date" placeholder="110/01" v-model="itemData">
          <label for="name">商品名稱：</label>
          <input type="text" id="name" name="name" placeholder="水費" v-model="itemName">
          <label for="price">商品價格：</label>
          <input type="number" id="price" name="price" placeholder="100.10" v-model="itemPrice">
        </div>
        <div class="button_IO">
          <button type="submit">輸入</button>
          <button type="button">查詢</button>
        </div>
      </fieldset>
    </form>
    <hr color="#959ccc"  width="80%" size="3px"/>


    <div id="app" class="output">
      <button v-on:click="handleClick" class="but2">物價表</button>
      <table class="show">
        <thead>
        <tr class="out">
          <th>日期</th>
          <th>商品名稱</th>
          <th>商品價格</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="item in shoppingList" class="data">
          <td>{{ item.date }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.price }}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      itemData: null,
      itemName: null,
      itemPrice: null,
      shoppingList: [
        // {  }
      ]
    }
  },
  methods: {
    addItem(){
      let item = {
        date: this.itemData,
        name: this.itemName,
        price: this.itemPrice
      }
      this.shoppingList.push(item)
      this.itemData = null
      this.itemName = null
      this.itemPrice = null
    }
  }
}
</script>

<style scoped>
  body{
    background: #12bd78;
  }
  .background_color{
    background: #c4ffb2;
    border-radius: 10px;
    height: 690px;
    box-shadow: 0 0 8px rgba(0, 0, 0, 0.3);
  }
  .head{
    font-family: 幼圆;
    /*background: lightgreen;*/
    padding: 0 0 0 0;
    margin: 0 0 0 0;
  }
  form {
    display: flex;
    align-items: center;
    justify-content: center;
    /*gap: 50px;*/
    padding: 25px 0 15px 0;
    /*background: #FFFF;*/
  }
  input, .MdFormGroup01{
    border-color: #2bd71c;
    border-width: 3px;
    font-family: 幼圆;
  }
  input{
    padding: 3px;
  }
  .MdFormGroup01{
    padding: 15px;
    background-color: rgb(113, 255, 66);
    /*border-radius: 10px;*/
    /* 陰影 */
    box-shadow: 0 0 2px rgba(0, 0, 0, 0.3);
  }
  p{
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 幼圆;
  }
  .button_IO{
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 10px 0 0 0;
    gap: 0px 50px;
  }
  .but2 {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: medium;
    background: #2bd71c;
    color: white;
    border-style: solid;
    border-color: #fffb00;
    border-width: 1px;
    border-radius: 50px 0 50px 0;
    width: 400px;
    padding: 3px 0 3px 0px;
  }
  .output {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 50px 0 0 0;
    /*background: #FFFF;*/
  }
  .out {
    background: #90eed5;
    color: #1c8111;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0px 120px;
    padding: 10px 20px 10px 20px;
    font-family: 幼圆;
    font-size: medium;
    border-radius: 20px;
  }
  .show {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 5px;
    padding: 15px 0;
    text-align: center;
    table-layout: fixed;
    border-collapse: collapse;
  }
  p, label, input, button{
    font-family: 幼圆;
    font-weight: 600;
  }
  .data {
    color: #1c8111;
    display: flex;
    gap: 0px 135px;
    padding: 10px ;
    font-family: 幼圆;
  }
</style>