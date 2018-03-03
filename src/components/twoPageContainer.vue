<template>
  <div class="tabNav">
    <transition class="animation" name="forward">
      <div class="forward" v-show="showList === 0"
      key="forward">
        <ul class="list">
          <li v-for="(item,index) in (dataList ? dataList.forward:list.forward)"
          :key="index"
          class="listItem">
            <span>
              <img class="itemImg" :src="item.img" alt="pic1">
              <div class="content">
                <span class="itemRank">{{item.rank}}</span>
                <span class="itemText">{{item.text}}</span>
              </div>
            </span>
          </li>
        </ul>
      </div>
    </transition>
    <transition class="animation" name="reverse">
      <div class="reverse" v-show="showList === 1"
        key="reverse">
        <ul class="list">
          <li v-for="(item,index) in (dataList ? dataList.reverse:list.reverse)"
          :key="index"
          class="listItem">
            <span>
              <img class="itemImg" :src="item.img" alt="pic1">
              <div class="content">
                <span class="itemRank">{{item.rank}}</span>
                <span class="itemText">{{item.text}}</span>
              </div>
            </span>
          </li>
        </ul>
      </div>
    </transition>
    <hr>
    <div class="indicators">
      <div class="indicator">
        <i class="indi1"
        :class="{'active':showList === 0}" 
        @mouseover="showList = 0"></i>
        <i class="indi2"
        :class="{'active':showList === 1}" 
        @mouseover="showList = 1"></i>
      </div> 
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      showList:0,
      list:{
        'forward':[
          {
            "img":"https://img11.360buyimg.com/mobilecms/s160x160_jfs/t6625/180/916393038/294602/1ed9a51b/59478622N5a819720.jpg!q90.webp",
            "rank":1,
            "text":"剑南春 水晶剑 52度 整箱装白酒 500ml*6瓶 口感浓香型",
          },
          {
            "img":"https://img11.360buyimg.com/mobilecms/s160x160_jfs/t5938/275/5738789059/127927/f0f2e7d1/596d66d8N179f55be.jpg!q90.webp",
            "rank":2,
            "text":"牛栏山 珍品二十 52度 整箱装 450ml*6瓶",
          },
          {
            "img":"https://img13.360buyimg.com/mobilecms/s160x160_jfs/t7270/64/1653194848/143684/2419538e/599fe41bN3cda444c.jpg!q90.webp",
            "rank":3,
            "text":"江小白 Se.100 40度 100ml*12瓶 整箱装白酒（小瓶装清香型高粱酒）",
          },
        ],
        'reverse':[
          {
            "img":"https://img20.360buyimg.com/mobilecms/s160x160_jfs/t10909/237/1671419420/364289/2014c5de/59e43868Ndc750454.jpg!q90.webp",
            "rank":4,
            "text":"牛栏山 白酒 二锅头 百年陈酿（三牛）42度 浓香型 单瓶装 400ml",
          },
          {
            "img":"https://img11.360buyimg.com/mobilecms/s160x160_g14/M08/01/01/rBEhV1NfXIQIAAAAAAFG5PYDsXEAAMyBAKVtcgAAUb8479.jpg!q90.webp",
            "rank":5,
            "text":"牛栏山 二锅头桶装 62度 5L",
          },
          {
            "img":"https://img12.360buyimg.com/mobilecms/s160x160_jfs/t2737/143/1426663177/121378/1579850b/573ea0e6Neb8b8ebd.jpg!q90.webp",
            "rank":6,
            "text":"茅台集团 习酒 红习酱1952 53度500ml*6瓶 整箱装白酒 口感酱香型",
          },
        ],

      }
    }
  },
  props:["dataList"],
  watch:{
    showList (old,curr) {
      const animation = Array.prototype.slice.call(document.getElementsByClassName("animation"),0)
      const prev = animation[old]
      const now = animation[curr]
      if (curr > old) {
        prev.style = "name:forward"
        now.style = 'name:reverse'
      } else {
        prev.style = "name:reverse"
        now.style = "name:forward"
      }
      

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
    height:450px;
    background:#fff;
    position: relative;
    overflow:hidden;
    .forward,
    .reverse {
      width:100%;
      height:80%;
      padding:0 20px;
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
                line-height:1;
                font-size:20px;
                white-space:wrap;
                word-wrap: break-word;
                word-break: break-all;
            }

          }
          
        }
      }



    }
    .indicators {
      width:100%;
      height:50px;
    
      position:absolute;
      bottom:0;
      
      .indicator {
        width:20%;
        margin:0 auto;
        height:100%;
        font-size:0;
        .indi1,
        .indi2 {
          position: relative;
          display: inline-block;
          height:16px;
          width:16px;
          margin:0 10px;
          border-radius:50%;
          cursor: pointer;
          &:after {
            content:'';
            position: absolute;
            display: block;
            width:5px;
            height:5px;
            top:1px;
            left:1px;
            border-radius: 50%;
            border:4px solid #eee;
          }
        }
        .active {
          background: #fdd9dd;
          &:after {
            position:absolute;
            top:2.5px;
            left:2.5px;
            border:3px solid transparent;
            background:#eb3436;
          }
        }
      }

    }
    .forward-enter-active {
      transform: translateX(0);
      transition: all 1s ease;
    }
          
    .forward-leave-active {
        transform: translateX(-100%);
        transition: all 1s ease;
    }
          
    .forward-enter {
        transform: translateX(-100%)
    }
          
    .reverse-leave {
        transform: translateX(0)
    }
    .reverse-enter-active {
      transform: translateX(0);
      transition: all 1s ease;
    }
          
    .reverse-leave-active {
        transform: translateX(100%);
        transition: all 1s ease;
    }
          
    .reverse-enter {
        transform: translateX(100%)
    }
          
    .forward-leave {
        transform: translateX(0)
    }
  }
</style>
