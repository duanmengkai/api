<template>
  <div>
    <div>
      <button @click="hh" class="button">按钮</button>
    </div>
    <div v-show="show">
      <div>
        <table>
          <tr id="tr">
            <td>IMEI</td>
            <td>device</td>
            <td>message</td>
            <td>tel</td>
          </tr>
          <tr v-for="(item,index) in sky" :key="index">
            <td>{{item.IMEI}}</td>
            <td>{{item.device}}</td>
            <td>{{item.message}}</td>
            <td>{{item.tel}}</td>
          </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      sky: "",
      show: false
    };
  },
  created() {
    this.axios.get("http://localhost:60020/all").then(response => {
      // console.log(response.data);
      this.sky = response.data.data;
    });
  },
  methods: {
    hh() {
      this.show = !this.show;
    }
  }
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
}
table {
  margin: 20px;
  width: 100%;
  background-color: #eeeeee;
  border: 1px solid black;
  border-collapse: collapse;
}
td {
  text-align: center;
  width: 25%;
  line-height: 50px;
  border: 1px solid black;
}
#tr td {
  background-color: rgb(228, 190, 24);
}

.button {

  width: 270px;
  height: 40px; 
  border-width: 0px; 
  border-radius: 3px; 
  background: #6611f0; 
  cursor: pointer; 
  outline: none; 
  font-family: Microsoft YaHei; 
  color: rgb(218, 211, 211); 
  font-size: 17px; 

  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
</style>
