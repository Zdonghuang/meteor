<template>
  <div class="home">
    <h1>
      太阳能水位监测
    </h1>
    <img src="/solar.png" class="solar">
    <img src="/mobile2.png" width="20%" class="second">
    <div class="water">
      <span>water</span>
      <div class="children"></div>
    </div>
    <p class="line"></p>
    <span class="texts">水位传感器</span>
    <div class="waterPipes">
      <div class="waterchild"></div>
      <span>水管</span>
      <p class="famen"></p>
      <p class="texte">电动阀门</p>
      <p class="famen1"></p>
    </div>
    <div class="mobileimg">
      <span>water</span>
      <div class="child"></div>
    </div>
    <p class="waterline">当前水位: <span class="waterHeight">100%</span></p>
    <button class="waterbtn">上水</button>
    <button class="waterstop">停止</button>
    <button class="btn" @click="animation">功能演示</button>
  </div>
</template>

<script>
// import { Meteor } from 'meteor/meteor'
export default {
  data () {
    return {
      ok:true,
      num:1,
      num2:1
    }
  },
  methods: {
    animation () {
      let child =document.getElementsByClassName('child')[0];
      let children =document.getElementsByClassName('children')[0];
      let waterHeight =document.getElementsByClassName('waterHeight')[0];
      if(this.ok){
        this.ok = false;
        child.className = 'child childs';
        children.className = 'children childrens'
        var time= setInterval(()=>{
          waterHeight.innerHTML= 100 - 20 * this.num + '%';
          if(this.num<5){
            this.num++;
          }else{
            waterHeight.style.color='red'
            this.upwater();
            clearInterval(time);
            this.num=1;
          }
        },2400)
      }
    },
    upwater(){
      let waterchild = document.getElementsByClassName('waterchild')[0];
      let famen = document.getElementsByClassName('famen')[0];
      let famen1 = document.getElementsByClassName('famen1')[0];
      let children = document.getElementsByClassName('children')[0];
      let child = document.getElementsByClassName('child')[0];
      let waterHeight = document.getElementsByClassName('waterHeight')[0];
      let waterbtn = document.getElementsByClassName('waterbtn')[0];
      let waterstop = document.getElementsByClassName('waterstop')[0];
      let texte = document.getElementsByClassName('texte')[0];
      var time1 = setTimeout(()=>{
        waterbtn.style.background = 'red';
        clearTimeout(time1);
      },400)
      var time2 = setTimeout(()=>{
        famen.style.top= '-40px';
        famen1.style.top= '-36px';
        texte.innerHTML='电动阀门开启';
        var i = 1;
        var time3 =setInterval(()=>{
          waterchild.style.width = i *20 +'%';
          if(i<5){
            i++;
          }else{
            clearInterval(time3)
          }
        },200)
        clearTimeout(time2);
      },800)
      var time4 = setTimeout(() => {
        children.className='children childrens childrenss'
        child.className = 'child childs childss'
        var time6 =setInterval(()=>{
          waterHeight.innerHTML = this.num2*20+'%';
          waterHeight.style.color='black'
          if(this.num2<5){
            this.num2++;
          }else{
            clearInterval(time6)
            this.num2=1;
          }
        },2400)
        clearTimeout(time4);
      }, 1800);
      var time5 = setTimeout(() => {
        waterchild.style.width='0%';
        famen.style.top= '-30px';
        famen1.style.top= '-26px';
        texte.innerHTML='电动阀门';
        waterbtn.style.background = '#62c99b';
        waterstop.style.background = 'red';
        clearTimeout(time5);
      }, 13800);
      var time7 = setTimeout(() => {
        waterstop.style.background = '#62c99b';
        this.ok=true;
        clearTimeout(time7);
      }, 14200);
    },
  },
}
</script>


<style lang="less">
.home {
  text-align: center;
  width: 1000px;
  margin: 0 auto;
  height: 100%;
  position: relative;
}
main{
  background-color: transparent;
  width: 1200px !important;
  padding: 0 !important;
  min-width: 1200px !important;
  margin: 20px auto !important;
  height: 670px;
  box-shadow: 0 0 10px #333;
  background-color: #fff;
}
img.second{
  float: right;
  margin-top: 50px;
  margin-right: 40px;
}

.water{
  position: absolute;
  top: 112px;
  left: 6px;
  width: 132px;
  height: 132px;
  border-radius: 50%;
  text-align: center;
  font-size: 22px;
  overflow: hidden;
  border:1px solid #333;
  background-color: #fff;
  transform: rotateY(30deg);
}
.water span{
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1000000;
  width: 100%;
  height: 100%;
  line-height: 132px;
  text-align: center;
}
.water .children{
  width: 100%;
  height: 100%;
  position: absolute;
  bottom: 0;
  left: 0;
  background-color: skyblue;
}
.mobileimg{
  position: absolute;
  top: 200px;
  right: 90px;
  width: 90px;
  height: 90px;
  border-radius: 50%;
  font-size: 18px;
  overflow: hidden;
  border: 1px solid #333;
}
.mobileimg span{
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1000000;
  width: 100%;
  height: 100%;
  line-height: 90px;
  text-align: center;
}
.mobileimg .child{
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: skyblue;
  line-height: 100%;
}
.waterline{
  position: absolute;
  width: 160px;
  font-size: 16px;
  top: 300px;
  right: 60px;
}
.waterbtn{
  width: 70px;
  height: 40px;
  font-size: 16px;
  line-height: 0px;
  position: absolute;
  top: 370px;
  right: 104px;
}
.waterstop{
  width: 70px;
  height: 40px;
  font-size: 16px;
  line-height: 0px;
  position: absolute;
  top: 420px;
  right: 104px;
}
.line{
  padding: 0;
  margin: 0;
  width: 6px;
  height: 40px;
  background-color: red;
  position: absolute;
  top: 236px;
  left: 64px;
  border-radius: 4px;
  z-index: 10000;
}
.texts{
  position: absolute;
  top: 280px;
  left: -44px;
  line-height: 18px;
  font-size: 22px;
  color: red;
  text-shadow: 2px 2px 4px #333;
}
.waterPipes{
  width: 132px;
  height: 10px;
  background-color: rgba(121, 119, 119, 0.692);
  position: absolute;
  top: 130px;
  left: -100px;
  border-radius: 0 4px 26px 0;
}
.waterchild{
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 0%;
  border-radius: 0 4px 20px 0;
  background-color: skyblue;
}
.waterPipes span{
  position: absolute;
  left: -28px;
  top: 8px;
  width: 100%;
  height: 100%;
  font-size: 22px;
  color: red;
  text-shadow: 2px 2px 4px #333;
}
.waterPipes p:nth-child(3){
  height: 4px;
  width: 20px;
  background-color: red;
  position: absolute;
  top: -30px;
  left: 50px;
}
.waterPipes p:nth-child(4){
  position: absolute;
  top: -80px;
  left: 10px;
  width: 150px;
  font-size: 22px;
  color: red;
  text-shadow: 2px 2px 4px #333;
}
.waterPipes p:nth-child(5){
  height: 20px;
  width: 4px;
  position: absolute;
  background-color: gold;
  top: -26px;
  left: 58px;
}
.btn{
  position: absolute;
  right: 90px;
  bottom: 70px;
}
.childs,.childrens{
  animation: animation 12s linear forwards;
}
.childss,.childrenss{
  animation: animations 12s linear forwards;
}
@keyframes animation {
  0%{
    height: 100%;
  }
  20%{
    height: 80%;
  }
  40%{
    height: 60%;
  }
  60%{
    height: 40%;
  }
  80%{
    height: 20%;
  }
  100%{
    height: 0%;
  }
} 
@keyframes animations {
  0%{
    height: 0%;
  }
  20%{
    height: 20%;
  }
  40%{
    height: 40%;
  }
  60%{
    height: 60%;
  }
  80%{
    height: 80%;
  }
  100%{
    height: 100%;
  }
} 

.solar{
   position: absolute;
   top: 88px;
   left: -88px;
   width: 700px;
}
</style>
