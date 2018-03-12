<template>
  <div class="scroller">
    <button class="backButton" @click="act(showList,'left')">
      <img src="/static/icons/Back_20px.png" class="backButtonImg" alt="Back">
    </button>
    <transition
    v-for="(item,index) in dataList"
    :key="'pics' + index"
    :name="isBorder  // 先判断是不是边界，再判断方向，再判断当前元素是进入还是退出，从而设定是左动画还是右动画
    // 这里是无限滚动的判断
    ? (isRight ? ( isNow(index) ? 'right' : 'left') : (isNow(index) ? 'left' : 'right'))
    : (isRight ? ( isNow(index) ? 'left' : 'right') : (isNow(index) ? 'right' : 'left'))">
     
      <div class="pics" v-show="showList === index">
        <img class="pic" :src="item" alt="pic">
      </div>
    </transition>
    <div class="indicators">
      <div class="indicator">
        <i v-for="(item,index) in dataList"
        :key="index"
        class="indi"
        :class="{'active':showList === index}"
        @mouseover="hover(index)"></i>
      </div> 
    </div>
    <button class="forwardButton" @click="act(showList,'right')">
      <img src="/static/icons/Forward_20px.png" class="forwardButtonImg" alt="Forward">
    </button>
  </div>
</template>
<script>
export default {
  data () {
    return {
      showList:0,
      oldList:-1,
      clickAble:true,
    }
  },
  props:["dataList"],
  watch:{
    showList (curr,old) {
      this.oldList = old
    }
  },
  mounted () {
    var p = this
    var div = document.getElementsByClassName('scroller')[1]
    var timer = setInterval(function() {
      p.act(p.showList,'right')
    },4000)
    div.addEventListener('mouseover',function () {
      clearInterval(timer)
    })
    div.addEventListener('mouseout',function () {
      timer = setInterval(function() {
        p.act(p.showList,'right')
      },2000)
    })

  },
  computed: {
    isBorder () {
      return Math.abs(this.showList - this.oldList) === this.dataList.length - 1
    },
    isRight () {
      return (this.oldList < this.showList) 
    }
  },
  methods: {
    act (now,direction) {
      var p = this
      if (this.clickAble) {
        this.clickAble = !this.clickAble
        if (direction === "left") {
          if (now === 0) {
            this.showList = this.dataList.length - 1
          } else {
            this.showList--
          }
        } else {
            if (now === this.dataList.length -1) {
              this.showList = 0
            } else {
              this.showList++
            }
        }
        setTimeout(function () {
          p.clickAble = !p.clickAble
        }, 200)
      }    
    },
    isNow (index) {
      return index === this.oldList
    },
    hover (index) {
      var p = this
      if (this.clickAble) {
        this.clickAble = !this.clickAble
        this.showList = index
      }
      setTimeout(function () {
        p.clickAble = !p.clickAble
      }, 0)
    }
  }
}
</script>
<style lang="less" scoped>
  * {
    margin:0;
    padding:0;
    border:0;
    outline:none;
  }

  .scroller {
    width:100%; 
    height:400px; 
    display: inline-block;
    background:#fff;
    position: relative;
    overflow:hidden;
    vertical-align: top;
    .backButton,
    .forwardButton {
      cursor: pointer;
      width:30px;
      height:60px;
      position: absolute;
      top:170px;
      z-index:1000;
      background:#000;
      opacity:0.4;
    }
    .forwardButton {
      right:0;
    }
    
    .pics {
      width:100%;
      height:95%;
      
      position:absolute;
      .pic {
        width:100%;
        height:95%;
        cursor: pointer;
        }

    }
    .indicators {
      width:100%;
      height:20px;
      position:absolute;
      bottom:10px;
      text-align:center;
      .indicator {
        width:100%;
        margin:0 auto;
        height:100%;
        font-size:0;
        text-align:center;
        .indi {
          position: relative;
          display: inline-block;
          height:15px;
          width:15px;
          margin:0 5px;
          border-radius:50%;
          cursor: pointer;
          &:after {
            content:'';
            position: absolute;
            display: block;
            width:8px;
            height:8px;
            top:1px;
            left:1px;
            border-radius: 50%;
            border:2px solid #b9beba;
          }
        }
        .active {
          background: #fdd9dd;
          &:after {
            position:absolute;
            top:2px;
            left:1.5px;
            border:2px solid transparent;
            background:#eb3436;
          }
        }
      }

    }
    .left-enter-active {
      transform: translateX(0);
      transition: all 0.6s ease;
    }
          
    .left-leave-active {
        transform: translateX(-100%);
        transition: all 0.6s ease;
    }
          
    .left-enter {
        transform: translateX(-100%)
    }
    .left-leave {
        transform: translateX(0)
    }  
    .right-leave {
        transform: translateX(0)
    }
    .right-enter-active {
      transform: translateX(0);
      transition: all 0.6s ease;
    }
          
    .right-leave-active {
        transform: translateX(100%);
        transition: all 0.6s ease;
    }
          
    .right-enter {
        transform: translateX(100%)
    }
    
    
  }
</style>
