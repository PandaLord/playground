<template>
  <div class="textBoard">
    <header>
      <div class="tags">
        <a class="tag1" @mouseover="selectTag(1)">促销</a>
        |
        <a class="tag2" @mouseover="selectTag(2)">公告</a>
        <div class="slideBar">

        </div>
        
      </div>
      <a class="more">更多</a>
    </header>
    <hr>
    <div class="promotion" v-show="selectedTag === 'promotion'">
      <ul class="list">
        <li v-for="(item,index) in promotionList"
        :key="index">
          {{item}}
        </li>
      </ul>
    </div>
    <div class="announcement" v-show="selectedTag === 'announcement'">
      <ul class="list">
        <li v-for="(item,index) in announcementList"
        :key="index">
          {{item}}
        </li>
      </ul>
    </div>  
  </div>
</template>
<script>
export default {
  data () {
    return {
      selectedTag:"promotion",
      promotionList:["开学季美瞳每满99减40","元宵美味1元起","暗影精灵3Pro首发抢购","数码好物0元试用"],
      announcementList:["京东启用全新客服电话“950618”","大家电订单超期自动取消公告","关于召回普利司通（天津）轮胎有限公司2个规格乘用车轮胎的公告","京东物流推出配送员统一外呼电话“95056”"],
    }
  },
  methods:{
    selectTag (index) {
      var tag= document.getElementsByClassName("tags")[0]
      if (index === 1) {
        this.selectedTag = "promotion"
      } else {
        this.selectedTag = "announcement"
      }
    }
  },
  watch: {
    selectedTag (old,curr) {
      var slider = document.getElementsByClassName("slideBar")[0]
      if (curr === "promotion") {        
        slider.style = "transform:translateX(42px);transition:all 0.6s ease"
      } else {
        slider.style = "transform:translateX(0);transition:all 0.6s ease"
      }
    }
  }
}
</script>
<style lang="less" scoped>
  * {
    padding:0;
    margin: 0;
    outline:0;
    border:0;
  }
  .textBoard {
    font-size:16px;
    width:160px;
    height:150px;
    background:#fff;
    color:#666;
    box-shadow: 0 2px 3px rgba(0,0,0,.1);
    header {
      width:100%;
      height:20px;
      .tags {
        float:left;
        display:inline;
        color:#999;
        line-height:1;
        .tag1,
        .tag2 {
          cursor: pointer;
        }
        .slideBar {
          position: relative;
          width:35px;
          left:0;
          margin-top:5px;
          height:3px;
          border-radius:25%;
          background: red;
        }
      }
      .more {
        float:right;
        cursor: pointer;
        &:hover {
          color:red;
        }
      }
    }
    .promotion,
    .announcement {
      width:100%;
      height:100px;
      
      .list {
        list-style:none;
        cursor: pointer;
        li {
          overflow:hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
          margin:10px 0;
          &:hover {
            color:red;
          }
        }

      }
    }
  }
</style>
