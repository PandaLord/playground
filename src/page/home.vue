<template>
  <div>
    <short-cut-header></short-cut-header>
    <search-bar></search-bar>
    <navbar></navbar>
    <div style="width:500px;">
      <rank-list-header></rank-list-header>
      <tabs></tabs>
      <two-page-container></two-page-container>
    </div>
    
    
    
  </div>
</template>
<script>
import Scroller from "../components/scroller.vue"
import Navbar from "../components/navbar.vue"
import ShortCutHeader from "../components/shortCutHeader.vue"
import searchBar from "../components/searchBar.vue"
import TwoPageContainer from "../components/twoPageContainer.vue"
import RankListHeader from "../components/rankListHeader.vue"
import Tabs from "../components/tabs.vue"

export default {
  data () {
    return {
      imgs:[
        "/static/pics/animatePics1.png",
        "/static/pics/animatePics2.png",
        "/static/pics/animatePics3.png",
        "/static/pics/animatePics4.png",
        "/static/pics/animatePics5.png",
        "/static/pics/animatePics6.png",
      ]
    }
  },
  components:{
    Scroller,
    Navbar,
    ShortCutHeader,
    searchBar,
    TwoPageContainer,
    RankListHeader,
    Tabs,
  }
  
}
</script>
<style lang="less" scoped>

</style>
