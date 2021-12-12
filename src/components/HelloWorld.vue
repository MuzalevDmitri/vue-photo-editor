<template>
<div><h1>Фоторедактор</h1></div>
<div class="box">
  <div class="images"> 
    <img :style="imgStyles" :class="[classImg]"  src="https://dootrix.com/wp-content/uploads/2019/03/image.png" alt=""> 
  </div>
  <div>

      <h1>Фильтры</h1>
      <div class="wrap">
    <button :class="classImg.sepia ? 'active' : ''" @click="classImg.sepia = !classImg.sepia">Сепия</button>
    <button :class="classImg.blur ? 'active' : ''" @click="classImg.blur = !classImg.blur">Блюр</button>
    <button :class="classImg.saturate ? 'active' : ''" @click="classImg.saturate = !classImg.saturate">Яркость</button>
    <button :class="classImg.anim ? 'active' : ''" @click="classImg.anim = !classImg.anim">Запустить кота</button>
    <button :class="classImg.a ? 'active' : ''" @click="classImg.a = !classImg.a">хрень</button>
    <button :class="classImg.hue? 'active' : ''" @click="classImg.hue = !classImg.hue">hue</button>
</div>
    
    <div class="sqr">
          <div>
      00<input type="range" 
      :min="imgSize.minWight"
      :max="imgSize.maxWidth"
      :value="imgSize.currentWidth"
      @input="imgSize.currentWidth = $event.target.value"
/>
          </div>
        Ширина
          <div>
         00<input type="range" 
         :min="imgSize.minHeight"  
         :max="imgSize.maxHeight"
         :value="imgSize.currentHeight"
         @input="imgSize.currentHeight = $event.target.value"
         />
         
         Высота
          </div>
    </div>

    
   </div>
</div>
</template>

<script>
export default {

  name: 'HelloWorld',
  data(){
      return {
        dtn: 'ret',
        classImg: {
          sepia: false,
          blur: false,
          saturate:false,
          anim: false,
          hue:false
        },
        imgSize:{
          minHeight:200,
          maxWidth:3000,
          maxHeight:2000,
          currentWidth:600,
          currentHeight:600,

          

        }
      }
  },
  computed:{
    imgStyles(){
      return{
        width: `${this.imgSize.currentWidth}px`,
        height: `${this.imgSize.currentHeight}px`
      }
    }

  }
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.box {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
  width: 900px;
  margin:  0 auto;
}

.sqr {
  width: 100%;
  display: flex;
  justify-content: center;
  margin-top: 50px;
  font-size: 25px;
}

.images {
  overflow: hidden;
  widows: 900px;
  height: 500px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.wrap {
  display: flex;
  flex-wrap: wrap;
}

.sqr div {
  margin-left: 60px;
}

input[type=range] {
  width: 200px;
}



.active {
  background:#000;
  color:#fff
}

button {
  background: none;
  border: 1px solid #000;
  padding: 10px 30px;
  margin: 0px 10px;
  font-size: 25px;
  cursor: pointer;
  transition: 0.6s;
  margin-top: 10px;

}

.anim {
    animation-name: rotation;
    animation-duration: 5s;
    animation-iteration-count: infinite;
    animation-timing-function: linear;
}

button:hover {
  background: #000;
color: #fff;

}

.sepia {
filter: sepia(100%)
}

.a {
  filter: hue-rotate(270deg)
}

.blur {
filter: blur(3px);
}

.hue{
  filter: hue-rotate(60deg);

}
.saturate {

filter: saturate(300%);
}

img{
  width: 100%;
}



h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

@keyframes rotation {
    0% {
        transform:rotate(0deg);
    }
    100% {
        transform:rotate(360deg);
    }
}
</style>
