<template>
  <div class="tabNav">
    <transition 
    v-for="(item,index) in list"
    :key="'rankList' + index"
    :name="(oldList < showList) ? (index === oldList ? 'left' : 'right') : (index === oldList ? 'right':'left')">
      <div class="rankList" v-show="showList === index">
        <ul class="list">
          <li v-for="(item,index) in (dataList ? dataList[index]:item)"
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
        <i v-for="(item,index) in list"
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
      list:[
        [
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
        [
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
        [
          {
            "img":"https://img11.360buyimg.com/mobilecms/s160x160_jfs/t6625/180/916393038/294602/1ed9a51b/59478622N5a819720.jpg!q90.webp",
            "rank":7,
            "text":"剑南春 水晶剑 52度 整箱装白酒 500ml*6瓶 口感浓香型",
          },
          {
            "img":"https://img11.360buyimg.com/mobilecms/s160x160_jfs/t5938/275/5738789059/127927/f0f2e7d1/596d66d8N179f55be.jpg!q90.webp",
            "rank":8,
            "text":"牛栏山 珍品二十 52度 整箱装 450ml*6瓶",
          },
          {
            "img":"https://img13.360buyimg.com/mobilecms/s160x160_jfs/t7270/64/1653194848/143684/2419538e/599fe41bN3cda444c.jpg!q90.webp",
            "rank":9,
            "text":"江小白 Se.100 40度 100ml*12瓶 整箱装白酒（小瓶装清香型高粱酒）",
          },
        ],
        [
          {
            "img":"https://img20.360buyimg.com/mobilecms/s160x160_jfs/t10909/237/1671419420/364289/2014c5de/59e43868Ndc750454.jpg!q90.webp",
            "rank":10,
            "text":"牛栏山 白酒 二锅头 百年陈酿（三牛）42度 浓香型 单瓶装 400ml",
          },
          {
            "img":"https://img11.360buyimg.com/mobilecms/s160x160_g14/M08/01/01/rBEhV1NfXIQIAAAAAAFG5PYDsXEAAMyBAKVtcgAAUb8479.jpg!q90.webp",
            "rank":11,
            "text":"牛栏山 二锅头桶装 62度 5L",
          },
          {
            "img":"https://img12.360buyimg.com/mobilecms/s160x160_jfs/t2737/143/1426663177/121378/1579850b/573ea0e6Neb8b8ebd.jpg!q90.webp",
            "rank":12,
            "text":"茅台集团 习酒 红习酱1952 53度500ml*6瓶 整箱装白酒 口感酱香型",
          },
        ],
        [
          {
            "img":"https://img11.360buyimg.com/mobilecms/s160x160_jfs/t6625/180/916393038/294602/1ed9a51b/59478622N5a819720.jpg!q90.webp",
            "rank":13,
            "text":"剑南春 水晶剑 52度 整箱装白酒 500ml*6瓶 口感浓香型",
          },
          {
            "img":"https://img11.360buyimg.com/mobilecms/s160x160_jfs/t5938/275/5738789059/127927/f0f2e7d1/596d66d8N179f55be.jpg!q90.webp",
            "rank":14,
            "text":"牛栏山 珍品二十 52度 整箱装 450ml*6瓶",
          },
          {
            "img":"https://img13.360buyimg.com/mobilecms/s160x160_jfs/t7270/64/1653194848/143684/2419538e/599fe41bN3cda444c.jpg!q90.webp",
            "rank":15,
            "text":"江小白 Se.100 40度 100ml*12瓶 整箱装白酒（小瓶装清香型高粱酒）",
          },
        ],
      ]
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
    height:450px;
    background:#fff;
    position: relative;
    overflow:hidden;
    .rankList {
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

if (old < curr) {
  if (index === old) {
    left
  } else {
    right
  } 
} else {
  if (index === old) {
    right
  } else {
    left
  }
}
(oldList < showList) ? (index === oldList ? 'left' : 'right') : (index === old ? 'right':'left')