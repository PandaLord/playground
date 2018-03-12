<template>
  <div class="searchBar">
    <div class="inputArea">
      <input class="searchInput"  placeholder="奥克斯空调"/><button class="searchButton">
        <img class="search" src="/static/icons/Search_50px.png" alt="serachIcon" />
      </button>
      <div class="searchBottom">
        <a v-for="(item,index) in searchbottom"
        :key="index"
        class="searchBottomItem">
          {{item}}
        </a>
      </div>
    </div>
    <button class="cartButton">
      <img class="cart" src="/static/icons/Cart_30px.png" alt="cartIcon"/>
      我的购物车
    </button>
    
    
    

  </div>
</template>
<script>
export default {
  data () {
    return {
      searchbottom:["抽10亿神券","12期免息","新鲜蔬菜","领券减千","50减40券","早春男装"]
    }
  }
}
</script>
<style lang="less" scoped>
  * {
    margin:0;
    padding:0;
    outline:none;
    border:none;
    
  }
  .searchBar {
    font-size:20px;
    width:900px;
    height:80px;
    margin-bottom:20px;//测试用css
    margin:0 auto; //测试用css
    .inputArea {
      display:inline-block;
      
      .searchInput {
        width:450px;
        height:40px;
        margin-left:60px;
        
      }
    }
    
    .searchButton {
      display:inline;
      width:80px;
      height:40px;
      background:#f10215;
      vertical-align: bottom;
      cursor: pointer;
      .search {
        width:25px;
        height:25px;
        
      }
    }
    .cartButton {
      float:right;
      cursor: pointer;
      width:200px;
      line-height: 40px;
      display:inline;
      background:#fff;
      color:red;
      vertical-align: middle;
      height:40px;
      .cart {
        vertical-align:text-top;
      }
    }
    .searchBottom {
      width:600px;
      height:20px;
      margin-left:60px;
      .searchBottomItem {
        font-size:0.8em;
        cursor: pointer;
        color:#999;
        margin:0 2px;
        &:hover {
          color:red;
        }
        &:first-child {
          color:red;
        }
        
      }
    }
  }
</style>
