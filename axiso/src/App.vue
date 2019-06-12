<template>
  <div id="app">
    <div class="bod">
    <button @click="kaishi()" class="button"> 开始 </button>
    <tr class="cont">
      <td>id</td>
      <td>imei</td>
      <td>device</td>
      <td>message</td>
      <td>tel</td>
    </tr>
    <tr v-for="index in syk" class="cont">
<td>{{ index.id }}</td>
<td>{{ index.IMEI }}</td>
<td>{{ index.device }}</td>
<td>{{ index.message }}</td>
<td>{{ index.tel }}</td>
    </tr>
    </div>
  </div>
</template>

<script>

export default {
  data(){
    return{
      syk:''
    }
  },
 
   methods:{
      kaishi(){
          this.axios.get('http://localhost:60020/all').then((response) => {
      console.log(response.data);
      this.syk=response.data.data
    })

      }
  }
}

</script>

<style>
.biao{
  width: 100px;
}
.biao td{
  border: 1px solid red;
}
#app{
  width: 100%;
}
.bod{
  width: 800px;
  margin: 0 auto;
}
.button{
   display: block;
  margin: 0 auto;
  width: 100px; 
  height: 30px;
  border-radius: 20px;
  background-color: aquamarine;
}
.cont{
  display: flex;
  width: 800px;
  height: 30px;
  background-color: aqua;
  border: 1px solid red;
}
.cont td{ 
    border: 1px solid red;
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;

}
</style>
