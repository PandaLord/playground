<template>
  <div>
      <ul class="list">
        <li class="listItem" v-for="(item,index) in (dataList ? dataList : list)"
        :key="index"
        :class="{'selected':index === selectedTag}"
        @mouseover="changeTab(index)">
          {{item}}
        </li>
      </ul>
    </div>
</template>
<script>
export default {
  data () {
    return {
      list:["白酒","手机通讯","厨房小电","大 家 电","清洁用品"],
      selectedTag:0
    }
  },
  props:['dataList'],
  methods:{
    changeTab (index) {
      this.selectedTag = index
      this.$emit("changeTab",index)
    }

  }
}
</script>
<style lang="less" scoped>
  * {
    padding:0;
    margin: 0;
    outline:none;
    border:0;
  }
  .list {
    width:100%;
    height:30px;
    background:#e3e4e5;
    
    list-style:none;
    .listItem {
      vertical-align: middle;
      display: inline;
      margin:0 20px;
      cursor: pointer;


    }
    

  }
  .selected {
      color:red;
  }

</style>

