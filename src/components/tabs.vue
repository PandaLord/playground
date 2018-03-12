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
      list:["白酒","大 家 电","厨房小电","手机通讯","清洁用品"],
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
    white-space:nowrap;
    
    
    .listItem {
      vertical-align: middle;
      word-wrap: break-word;
      text-overflow: ellipsis;
      word-break:break-all;
      width:20%;
      display: inline;
      margin:0 10px;
      cursor: pointer;
      font-size:14px;
    }
    

  }
  .selected {
      color:red;
  }

</style>

