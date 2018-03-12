<template>
  <div class="subListHeader">
      <h3 class="title">{{headerData ? headerData.title : header.title}}</h3>
      <a :href="headerData ? header.jumpPage :header.jumpPage" class="jump">
        <img class="pointer" :src="headerData ? header.imgSrc :header.imgSrc" alt="pointer">
        <span class="text">{{headerData ? header.text :header.text}}</span>
      </a>
  </div>
</template>
<script>
export default {
  data () {
    return {
      header:{
        'title':"排行榜",
        "jumpPage":"http://www.baidu.com",
        "imgSrc":"/static/icons/Next_25px.png",
        "text":"专属你的购物指南"
      }
    }
  },
  props:["headerData"]
}
</script>
<style lang="less" scoped>
  * {
    margin:0;
    padding:0;
    border:0;
    outline:none;
  }
  .subListHeader {
    width:100%;
    height:50px;
    box-sizing:border-box;
    background:#fff;
    text-align:left;
    
    padding:10px 15px;
    display:inline-block;
    .title {
      display: inline;
      font-size:20px;
      line-height: 20px;
      
    }
    .jump {
      text-decoration: none;
      &:visited {
        color:inherit;
      }
      .pointer {
        font-size:0;
        vertical-align: text-bottom;
        line-height:20px;
        width:24px;
        height:24px;
      }
      .text {
        font-size:15px;
        line-height:20px;
        color:#666;
        vertical-align:text-top;
        
      }
    }

  }
</style>
