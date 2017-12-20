<template>
  <div class="left">
      <header>菜谱</header>
      <div class="main">
          <div :class="{item:true, active:isShow(i)}" v-for='(v, i) in cddata' @click='Pclick(i)'> 
              {{ v.name }}
          </div>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      lmsg: "我是left的msg",
      cddata:cd.list,
      index:0
    }
  },
  methods:{
      Pclick(i){
          this.index = i;
          this.$emit('CLclick', this.index)
      },
      isShow(i){
          return this.index === i;
      }
  }
};
</script>

<style scoped>
    header{
        font-size: 20px;
        line-height: 50px;
        font-weight: bold;
        color: white;
        border:3px solid #CA8755;
        border-radius: 10px;
        background-color: #E6C5AC;
    }
    .main{
        margin-top: 10px;
        height: 475px;
        text-align: center;
        overflow: auto;
        box-shadow: 0px 0px 4px 4px #F4E6DD;
        border-radius: 10px;
        padding: 20px 0px 15px;
    }
    
    .item{
        width: 70%;
        font-size: 16px;
        line-height: 28px;
        color: #CC8E62;
        background-color: #F6E8DE;
        border-radius: 5px;
        margin-bottom: 5px;
        display: inline-block;
    }
    .item:hover{
        width: 80%;
        color: #FDFCFC;
        background-color: #E6C5AC;
        cursor: pointer;
        transition:all 1s linear 500
    }
    .active{
        width: 70%;
        color: #FDFCFC;
        background-color: #CC8E62;
    }
</style>
