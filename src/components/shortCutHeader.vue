<template>
  <header class="header">
    <div class="viewport">
      <span class="selectProvince"
      @mouseover="showProvinceSelect = true"
      @mouseout="showProvinceSelect = false">
        <img class="pin" src="/static/icons/pin_20px.png" alt="城市选点指针" />
          {{selectedProvince}}
        <div class="provincesList"
          v-show="showProvinceSelect">
          <ul v-for="(item,index) in provinces"
            :key="index"
            class="provinceCol">
            <li v-for="(pros,index) in item"
            :key="'pros' + index"
            class="provinceItem"
            @click="selectedProvince = pros"
            :class="{'selected':pros === selectedProvince}">
              {{pros}}
            </li>
          </ul>
        </div>
      </span>
      <ul class="shortcutList">
        <li v-for="(item,index) in list"
        :key="index"
        :class="'item' + index"
        class="headerItem"
        @mouseover="branch = index"
        @mouseout="branch = -1">
          {{item}}
          <div v-if="index === 2" class="myJd" v-show="branch === 2">
            <div class="myJdBranch">
              <ul class="branchList">
                <li class="branchItem">待处理订单</li>
                <li class="branchItem">返修退换货</li>
                <li class="branchItem">降价产品</li>
              </ul>
              <ul class="branchList">
                <li class="branchItem">消息</li>
                <li class="branchItem">我的问答</li>
                <li class="branchItem">我的关注</li>
              </ul>
            </div>
            <hr>
            <div class="myJdBranchS">
              <ul class="branchList">
                <li class="branchItem">我的京豆</li>
                <li class="branchItem">我的白条</li>
              </ul>
              <ul class="branchList">
                <li class="branchItem">我的优惠卷</li>
                <li class="branchItem">我的理财</li>
              </ul>
            </div>
            
          </div>
          <div v-if="index === 5" class="customerService" v-show="branch === 5">
            <div class="customerServiceBranch">
              <h3>客户</h3>
                <ul class="branchList">
                  <li class="branchItem">帮助中心</li>
                  <li class="branchItem">在线客服</li>
                  <li class="branchItem">电话客服</li>
                  <li class="branchItem">金融咨询</li>
                </ul>
                <ul class="branchList">
                  <li class="branchItem">售后服务</li>
                  <li class="branchItem">意见建议</li>
                  <li class="branchItem">客服邮箱</li>
                  <li class="branchItem">售全球客服</li>
                </ul>
            </div>
            <hr>
            <div class="customerServiceBranch">
              <h3>商户</h3>
              <ul class="branchList">
                <li class="branchItem">合作招商</li>
                <li class="branchItem">商家后台</li>
                <li class="branchItem">商家帮助</li>
              </ul>
              <ul class="branchList">
                <li class="branchItem">学习中心</li>
                <li class="branchItem">京麦工作台</li>
                <li class="branchItem">规则平台</li>
              </ul>
            </div>     
          </div> 
        </li>
      </ul>
    </div>
    
  </header>

</template>
<script>
export default {
  data () {
    return {
      list:["免费注册","我的订单","我的京东","京东会员","企业采购","客户服务","网站导航","手机京东"],
      selectedProvince:"北京",
      branch:-1,
      showProvinceSelect:false,
      provinces:[
        ["北京","山西","内蒙古","福建","江西","西藏","新疆"],
        ["上海","河南","江苏","湖北","四川","陕西","港澳"],
        ["天津","辽宁","山东","湖南","海南","甘肃","台湾"],
        ["重庆","吉林","安徽","广东","贵州","青海","钓鱼岛"],
        ["河北","黑龙江","浙江","广西","云南","宁夏","海外"],
      ],

    }
  }
  
}
</script>
<style lang="less" scoped>
  * {
    margin:0;
    padding:0;
  }
  .header {
    font-size:16px;
    width:100%;
    height:30px;
    line-height:30px;
    color:#999;
    border-bottom: 1px solid #ddd;
    margin-bottom:40px; //测试css
    background-color: #e3e4e5;
    .viewport {
      width:1000px;
      margin:0 auto;
      height:100%;
      
      .selectProvince {
        float:left;
        vertical-align: middle;
        color:red;
        
        position:relative;
        .pin {
          vertical-align: text-bottom;
        }
        .provincesList {
          color:#999;
          width:300px; 
          background:#fff;
          position: absolute;
          z-index:1000;
          top:30px;
          left:0;
          .provinceCol {
            display:inline-block;
            width:15%;
            margin:7px;
            text-align:left;
            white-space:nowrap;
            .provinceItem {
              float:left;
              list-style:none;
              cursor: pointer;
              padding:2px 5px;
              &:hover {
                color:red;
                background:#eee;
              }
            }
            .selected {
              background-color: #f10215;
              color: #fff;
              &:hover {
                background-color: #f10215;
                color: #fff;
              }
            }
          }
          


        }
      }
      .shortcutList {
        display:inline;
        width:85%;
        float:right;
        list-style: none;
        .headerItem {
          display: inline;
          position:relative;
          width:8%;
          padding:5px 0;
          cursor: pointer;
          .myJd {
            position:absolute;
            z-index:1000;
            top:32px;
            left:6px;
            height:170px;
            width:200px;
            color:#999;
            cursor:pointer;
            padding:5px 10px;
            background:#fff;
            border:1px solid #ddd;
            hr {
              margin:10px 0;
            }
            .branchList {
              list-style: none;
              display:inline-block;
              white-space:nowrap;
              width:40%;
              margin-right:15px;
              height:100%;
              .branchItem:hover {
                color:red;
              }
            }
          }
          .customerService {
            position:absolute;
            z-index:1000;
            top:32px;
            right:0;
            height:300px;
            width:200px;
            color:#999;
            cursor:pointer;
            padding:5px 10px;
            background:#fff;
            border:1px solid #ddd;
            hr {
              margin:10px 0;
            }
            
            .branchList {
              list-style: none;
              display:inline-block;
              white-space:nowrap;
              width:40%;
              margin-right:15px;
              height:100%;
              .branchItem:hover {
                color:red;
              }
            }
          }
          &:hover {
            color:red;
          }
          &:first-child {
            color:red;
            white-space:nowrap;        
            &:before {
              content:"您好,请注册";
              margin-right:10px;
              color:#999;  
            }
            &:hover::before{
                color:red;
            }        
          }
          &:not(:first-child) {
            &:before {
              content:"|";
              margin:0 3px;
            }
          }
          &:nth-child(3):after,
          &:nth-child(6):after {
            content:"v";
            margin:0 2px;
          }
          
                 
        }
      }
    }

    

  }
</style>
