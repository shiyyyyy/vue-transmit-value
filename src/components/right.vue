<template>
  <div class="right" @click='cc'>
    <header>购物车</header>
    <div class="footer">
      <div class="main">
        <div class="item" v-for='(v, i) in Cv'> 
          <div class="content">
            <div class="name">
              <span>{{ v.ellipsis }}{{"x" + num[i] }}</span>
            </div>
            <div class="rmb">
               <span>{{ "¥" + Math.ceil(num[i]*v.price*100)/100 }}</span>
               <!-- ¥:250 -->
            </div>
            <img src="../assets/X.png" @click.stop='cancel(i)'></img>
          </div> 
        </div>
      </div>
      <div class="buy">
        <p>总价:¥{{rmb}}</p>
        <span>购买</span>
        <span @click.stop='creat'>清除</span>
      </div>
    </div>
  </div>
</template>

<script>
import bus from "../bus";
export default {
  data() {
    return {
      rmsg: "我是right的msg",
      cddata: cd.list,
      rmb: 0
    };
  },
  methods: {
    cc() {
      console.log(this);
      console.log(bus);
    },
    cancel(i) {
      this.Cv.splice(i, 1);
    },
    creat() {
      this.$emit("ceartArr", this.Cv);
      this.Cv = [];
    }
  },
  props: ["ind", "Cv", "num"],
  watch: {
    Cv: function(val, oldval) {
      this.rmb = 0;
      for (var i = 0; i < this.Cv.length; i++) {
        this.rmb += this.Cv[i].price * this.num[i];
        this.rmb = Math.ceil(this.rmb * 100) / 100;
      }
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
  border: 3px solid #4b55ab;
  border-radius: 10px;
  background-color: #a4aad4;
}
.footer {
  margin-top: 10px;
  height: 475px;
  text-align: center;
  overflow: auto;
  box-shadow: 0px 0px 4px 4px #d9daec;
  border-radius: 10px;
  padding: 20px 0px 15px;
}
.main {
  height: 375px;
  overflow: auto;
  border-bottom: 1px solid #4b55ab;
}

.item {
  width: 70%;
  font-size: 16px;
  line-height: 28px;
  color: #6c57ac;
  background-color: #dbddee;
  border-radius: 5px;
  margin-bottom: 5px;
  display: inline-block;
}
.item:hover {
  width: 80%;
  color: #fdfcfc;
  background-color: #e6c5ac;
  cursor: pointer;
  transition: all 1s linear 500;
}

.content {
  display: flex;
  justify-content: space-around;
  align-items: center;
  position: relative;
}
.content .name {
  width: 50%;
  height: 100%;
  text-align: center;
}
.content .name span {
  line-height: 100%;
  display: inline-block;
}
.content .rmb {
  width: 40%;
  height: 100%;
}
.content img {
  width: 12px;
  height: 12px;
  position: absolute;
  top: 0px;
  right: 0px;
}

.buy {
  height: 99px;
  overflow: hidden;
}
.buy p {
  width: 100%;
  margin: 10px 0px;
  font-size: 20px;
  font-weight: bold;
}
.buy span {
  width: 35%;
  line-height: 30px;
  border-radius: 5px;
  display: inline-block;
}
.buy span:nth-child(2) {
  color: white;
  background-color: #6c57ac;
}
.buy span:nth-last-child(1) {
  background-color: #ccc;
}
</style>

