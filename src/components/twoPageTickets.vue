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
                <span class="itemValue">{{'$' + item2.value}}</span>
                <span class="itemLimit">{{'满'+ item2.limit + '元可用'}}</span>
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
    height:400px;
    background:#fff;
    position: relative;
    overflow:hidden;
    .rankList {
      width:100%;
      height:100%;
      padding:0 20px 10px 10px;
      position:absolute;
      .list {
        list-style:none;
        .listItem {
          margin-bottom:15px;
          width:100%;
          height:33%;
          background:#eee;
          cursor: pointer;
          white-space: nowrap;
          position:relative;
          &:before {
            content:'';
            position:absolute;
            top:-7.5px;
            right:15%;
            height:15px;
            width:15px;
            border-radius:50%;
            background:#fff;
          }
          &:after {
            content:'';
            position:absolute;
            bottom:-7.5px;
            right:15%;
            height:15px;
            width:15px;
            border-radius:50%;
            background:#fff;

          }
          .itemImg {   
            width:25%;
            height:100%;
            vertical-align:middle;
            border-radius:50%;
            margin-left:10px;
          }
          .content {   
            display:inline-block;
            color:#666;
            width:90%;
            height:33%;
            white-space:nowrap;
            margin-left:10px;
            overflow:hidden;
            vertical-align:middle;
            &:hover {
                color:#f10125;
            }
            &:after {
              content:'更多精选好券';
              width:14px;
              line-height:15px;
              font-size:14px;
              position:absolute;
              white-space:pre-wrap;
              top:-13%;
              margin-top:20px;
              right:8%;
              
            }
            .itemValue {
              font-size:30px;
              display: block;
              margin-top:10px;
              
            }
            .itemLimit {
              display: block;
            }
            .itemText {
                display: block;
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
      height:20px;
      position:absolute;
      bottom:15px;
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