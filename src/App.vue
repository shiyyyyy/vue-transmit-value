<template :data='cddata'>
  <div id="app" @click='change'>
    <left v-on:CLclick='CLclickIndex'> </left>
    <center v-on:CCclick='CCclickVal' v-on:CCklick='CCklickNum' :ind='Li' :crt='creatarr'></center>
    <right :Cv='Cv' :ind='Li' :num='num' v-on:ceartArr='creatArray'></right>
  </div>
</template>

<script>
import left from "./components/left";
import center from "./components/center.vue";
import right from "./components/right";
export default {
  name: "app",
  data() {
    return {
      msg: "App我最大~ ",
      cddata:cd.list,
      Li:0,
      Cv:'',
      num:[],
      creatarr:[]
    };
  },
  components: {
    left,
    center,
    right
  },
  methods:{
    change(){
      console.log(this)
    },
    CLclickIndex(data){
      this.Li = data;
      console.log(data)
    },
    CCclickVal(data){
      this.Cv = data;
    },
    CCklickNum(data){
      this.num = data;
    },
    creatArray(data){
      this.creatarr = data;
    }
  },
  props:['data']
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 100px auto 0px;
  width: 80%;
  display: flex;
  justify-content: space-around;
}
.left{
  width: 330px;
  height: 570px;
}
.center{
  width: 330px;
  height: 570px;
}
.right{
  width: 330px;
  height: 570px;
}


</style>
