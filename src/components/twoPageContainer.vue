<template>
  <div class="tabNav">
    <transition 
    v-for="(item,index) in dataList"
    :key="'rankList' + index"
    :name="(oldList < showList) ? (index === oldList ? 'left' : 'right') : (index === oldList ? 'right':'left')">
      <div class="rankList" v-show="showList === index">
        <ul class="list">
          <li v-for="(item2,index) in item"
          :key="index"
          class="listItem">
            <span>
              <img class="itemImg" :src="item2.img" alt="pic1">
              <div class="content">
                <span class="itemRank">{{item2.rank}}</span>
                <span class="itemText">{{item2.text}}</span>
              </div>
            </span>
          </li>
        </ul>
      </div>
    </transition>
    <hr>
    <div class="indicators">
      <div class="indicator">
        <i v-for="(item,index) in dataList"
        :key="index"
        class="indi"
        :class="{'active':showList === index}"
        @mouseover="showList = index"></i>
      </div> 
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      showList:0,
      oldList:-1,
    }
  },
  props:["dataList"],
  watch:{
    showList (curr,old) {
      this.oldList = old
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

  .tabNav {
    width:100%;
    height:370px;
    background:#fff;
    position: relative;
    overflow:hidden;
    .rankList {
      width:100%;
      height:80%;
      padding:0 20px;
      margin-top:20px;
      position:absolute;
      .list {
        list-style:none;
        .listItem {
          margin-bottom:15px;
          width:100%;
          height:33%;
          cursor: pointer;
          .itemImg {   
            width:25%;
            height:100%;
            vertical-align:middle;
          }
          .content {
            display:inline;
            color:#666;
            &:hover {
                color:#f10125;
            }
            .itemRank {
              font-size:60px;
              display: inline;
              margin:0 10px;
              vertical-align: middle;
              
            }
            .itemText {
                display: inline-block;
                vertical-align:middle;
                width:50%;
                height:40px;
                line-height:1;
                overflow:hidden;
                font-size:20px;
       
            }

          }
          
        }
      }



    }
    .indicators {
      width:100%;
      height:50px;
      position:absolute;
      bottom:-20px;
      
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
      transition: all 1s ease;
    }
          
    .left-leave-active {
        transform: translateX(-100%);
        transition: all 1s ease;
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
      transition: all 1s ease;
    }
          
    .right-leave-active {
        transform: translateX(100%);
        transition: all 1s ease;
    }
          
    .right-enter {
        transform: translateX(100%)
    }
          
    
  }
</style>