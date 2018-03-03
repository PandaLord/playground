<template>
  <div id="picsFrame">
    <transition-group tag="ul" id="picsContainer" name="pics">  
        <li v-for="(item,index) in imgSrc"
        :key="index"
        v-show="index === mark">
          <img class="animatePics" :src="item"/>
        </li>
    </transition-group>
    <ul id="sliders">
        <li :class="{'active':index  === mark }"
          v-for="(item,index) in imgSrc"
          :key="index"
          @click="animate(index)">
        </li>
    </ul>           
  </div>
</template>
<script>
export default {
  data () {
    return {
      mark:0, // 起始的slider点
      
    }
  },
  props:["arrow","imgSrc","width","height"],
  computed: {
    // imgs () {
    //   var len = this.imgSrc.length
    //   var first = this.imgSrc[0]
    //   // var last = this.imgSrc[len - 1]
    //   var newSrc = this.imgSrc
    //   newSrc.push(first)
    //   // newSrc.unshift(last)
    //   return newSrc
    // }
  },
  mounted () {
  
   var picsF = document.getElementById("picsFrame")
   var picsC = document.getElementById("picsContainer")
   var animatePics = document.getElementsByClassName("animatePics")
   picsF.style.height = this.height
   picsF.style.width = this.width
   
   Array.prototype.forEach.call(animatePics,element => {
     element.style.width = this.width
     element.style.height= this.height 
   }) 

   var timer = setInterval(this.auto,2000)
  },
  methods:{
    animate(index) {
      this.mark = index
    },
    auto () {
      if (this.mark !== this.imgSrc.length - 1) {
        this.mark++
      } else {
        this.mark = 0

      }
      
    }
  }
} 
</script>
<style lang="less" scoped>
  * {
    margin:0;
    padding:0;
  }
  #picsFrame { 
    position:relative;
    width:900px;
    height:450px;
    margin:0 auto; 
    overflow:hidden;
    margin-bottom:50px; // 测试用css
  }
  #picsContainer {
    width:900px;
    height:450px; // 这里如果不加width会垂直排列
    top:0;
    left:0;
    li {
      position: absolute;
    }
    
  }
  #sliders {
    position: absolute;
    bottom:5px;
    list-style:none; 
    left:350px;
    
    li {
      float:left;
      &:before {
        content: "";
        text-align:center;
        display: inline-block;
        margin-left: 7px;
        border: 12px solid rgba(0, 0, 0, 0.7);
        border-radius: 50%;
        cursor: pointer;
      }
              
    }
    .active::before {
          border-color: red;
    }  
  }
  .pics-enter-active {
      transform: translateX(0);
      transition: all 1s ease;
  }
        
  .pics-leave-active {
      transform: translateX(-100%);
      transition: all 1s ease;
  }
        
  .pics-enter {
      transform: translateX(100%)
  }
        
  .pics-leave {
      transform: translateX(0)
  }
  
  


</style>

