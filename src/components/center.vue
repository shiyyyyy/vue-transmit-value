<template>
  <div class="left" @click='cc'>
      <header>原料</header>
      <div class="main">
          <div :class='{item:true, active:isShow(i)}' v-for='(v, i) in cddata[ind].ellipsis' @click='Pclick(v,i)'> 
              <span>{{v.ellipsis}}</span>
              <span>{{'¥:' + v.price}}</span>
          </div>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cmsg: "我是center的msg",
      cddata: cd.list,
      rarr: [],
      num: [],
      index: ""
    };
  },
  methods: {
      cc(){
          console.log(this)
      },
    Pclick(v,i) {
      // 这个是当前选项
      this.index = i;
      // 这些是排除重复数组
      this.rarr.push(v);
      this.num.push(1);

      for (var k = 0; k < this.rarr.length; k++) {
        for (var j = k + 1; j < this.rarr.length; j++) {
          if (this.rarr[k] == this.rarr[j]) {
            this.num.splice(j, 1);
            ++this.num[k];
            this.rarr.splice(j, 1);
          }
        }
      }
      this.$emit("CCclick", this.rarr);
      this.$emit("CCklick", this.num);
    },
    isShow(i){
        return this.index === i;
    }
  },
  props: ["ind", 'crt'],
  watch:{
      "crt":function(){
          console.log(this.crt)
          this.rarr = [];
          this.num = [];
      }
  }
};
</script>

<style scoped>
header {
  font-size: 20px;
  line-height: 50px;
  font-weight: bold;
  color: white;
  border: 3px solid #725a67;
  border-radius: 10px;
  background-color: #b8acb2;
}
.main {
  margin-top: 10px;
  height: 475px;
  text-align: center;
  overflow: auto;
  box-shadow: 0px 0px 4px 4px #e2dee0;
  border-radius: 10px;
  padding: 20px 0px 15px;
}

.item {
  width: 70%;
  font-size: 16px;
  line-height: 28px;
  color: #796570;
  background-color: #e3dee0;
  border-radius: 5px;
  margin-bottom: 5px;
  display: inline-block;
}
.item:hover {
  width: 80%;
  color: #fcfcfc;
  background-color: #c7bdc2;
  cursor: pointer;
  transition: all 1s linear 500;
}
.active{
  width: 70%;
  color: #fcfcfc;
  background-color: #796570;
}
.item span:first-child{
    width: 55%;
    height: 100%;
    text-align: center;
    display: inline-block;
}
.item span:nth-last-child(1){
    width: 40%;
    display: inline-block;
}
</style>

