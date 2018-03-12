<template>
<div>
  <short-cut-header></short-cut-header>
  <div class="viewPort"> 
    <search-bar></search-bar>
    <div class="navPart" >
      <navbar></navbar>
      <scroller-l :data-list="imgL"></scroller-l>
      <text-board></text-board>
    </div>
    <div class="rankPart">
      <div class="rankList">
        <rank-list-header ></rank-list-header>
        <tabs @changeTab="changeTab"></tabs>
        <two-page-container 
          v-for="(item,index) in twoPageContainer"
          :key="index"
          v-show="twoPageContainerShow === index"
          :dataList="item">  
        </two-page-container>
      </div>
      <div class="vipAlbum">
        <rank-list-header 
        :header-data="{'title':'会买专辑','text':'甄选优质好物','jumpPage':'','imgSrc'
        :'/static/icons/Next_25px.png'}"></rank-list-header>
        <scroller-s :data-list="imgS"></scroller-s>      
      </div>
      <div class="tickets">
        <rank-list-header 
        :header-data="{'title':'领券中心','text':'前往领券中心','jumpPage':'','imgSrc'
        :'/static/icons/Next_25px.png'}"></rank-list-header>
        <two-page-tickets :data-list="twoPageTickets"></two-page-tickets>
      </div>
    </div>
  </div>
</div>
</template>
<script>
import ScrollerL from "../components/scrollerL.vue"
import Navbar from "../components/navbar.vue"
import ShortCutHeader from "../components/shortCutHeader.vue"
import searchBar from "../components/searchBar.vue"
import TwoPageContainer from "../components/twoPageContainer.vue"
import RankListHeader from "../components/rankListHeader.vue"
import Tabs from "../components/tabs.vue"
import ScrollerS from "../components/scrollerS.vue"
import TextBoard from "../components/textBoard.vue"
import TwoPageTickets from "../components/twoPageTickets.vue"
export default {
  data () {
    return {
      imgL:[
        'http://m.360buyimg.com/babel/jfs/t14437/184/2434094132/102153/7bc3b34b/5aa0d4b3Nbdb155d6.jpg'
        ,
        'http://img1.360buyimg.com/pop/jfs/t18187/148/647561551/79748/3c0429ac/5a9fb7dfN7d8bb591.jpg'
        ,
        'http://img1.360buyimg.com/pop/jfs/t15868/278/2271633165/88656/87b21095/5aa0a41eNc698c436.jpg'
        ,
        'http://m.360buyimg.com/babel/jfs/t16357/297/2210472556/91416/9c86d44a/5aa0f38cNc5872539.jpg'
        , 
        'http://img1.360buyimg.com/pop/jfs/t16243/206/2284987947/185285/3086eb4e/5aa23dbbN557b0923.jpg'
        ,       
        'http://m.360buyimg.com/babel/jfs/t15805/75/2351341791/41823/ed167836/5aa09e1dNd669466a.jpg'
        ,
        'http://m.360buyimg.com/babel/jfs/t17893/239/637260795/100280/d9fd6379/5a9e1186N3cffb5da.jpg'
        ,
        '//m.360buyimg.com/babel/jfs/t17200/273/645981689/55022/51447405/5a9e3545N4ec4b2e6.jpg'
        ,
      ],
      imgS:[
        '//img12.360buyimg.com/mobilecms/s700x600_jfs/t5614/299/3234894996/195378/66bb13cc/5938fb7eN8853f2e3.jpg!q90!cc_350x300.webp',
        '//img20.360buyimg.com/mobilecms/s700x600_jfs/t7591/211/3990219280/32266/13ac1ae3/5a4f2da2N3e63786f.jpg!q90!cc_350x300.webp',
        '//img12.360buyimg.com/mobilecms/s700x600_jfs/t14707/164/1771724103/19927/78dc2ed/5a576dc0N032dd4e0.jpg!q90!cc_350x300.webp',
      ],
      twoPageContainer:[
        [
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
          ]
        ],
        [
          [
            {
            "img":"https://img13.360buyimg.com/mobilecms/s80x80_jfs/t6583/360/144916161/277180/fce869e1/593a2a2bN923ddc83.jpg!q90.webp",
            "rank":1,
            "text":"创维（Skyworth）55M7 55英寸14核4K超高清智能酷开网络液晶电视（黑色）",
            },
            {
              "img":"https://img14.360buyimg.com/mobilecms/s80x80_jfs/t19261/102/567707348/105750/420087ac/5a950ffcNf095e1ca.jpg!q90.webp",
              "rank":2,
              "text":"美的（Midea）大1匹 空调挂机 冷暖 变频 超一级能效 壁挂式空调KFR-26GW/WCEN8A1@",
            },
            {
              "img":"https://img12.360buyimg.com/mobilecms/s80x80_jfs/t4936/88/2155716298/94966/64e2f89a/58f9c1bbN6965b210.jpg!q90.webp",
              "rank":3,
              "text":"美的(Midea)655升 变频风冷智能对开门冰箱 一级能效 中央智控 米兰金 远程操控 BCD-655WKPZM(E)",
            },
          ],
          [
            {
            "img":"https://img14.360buyimg.com/mobilecms/s80x80_jfs/t4279/73/3331786751/571457/88e75878/58dcc6ddN977fb394.jpg!q90.webp",
            "rank":4,
            "text":"小米（MI）小米电视4A 标准版 43英寸 HDR 2GB+8GB 四核64位处理器 全高清智能语音网络平板电视（L43M5-AZ）",
            },
            {
              "img":"https://img14.360buyimg.com/mobilecms/s80x80_jfs/t11542/159/363434643/169463/b5086ebe/59eea7c9N96f25d5d.jpg!q90.webp",
              "rank":5,
              "text":"小天鹅(LittleSwan) 10公斤变频滚筒洗衣机 BLDC电机十年包修 wifi智能控制 白色 TG100V20WD",
            },
            {
              "img":"https://img11.360buyimg.com/mobilecms/s80x80_jfs/t5122/310/1122668660/62705/9bd6b910/590bdf06N44d5654d.jpg!q90.webp",
              "rank":6,
              "text":"康佳（KONKA）170升 双门冰箱 金属面板 保鲜静音（银色）BCD-170TA ",
            },
          ]
        ],
        [
          [
            {
            "img":"https://img12.360buyimg.com/mobilecms/s80x80_jfs/t7195/168/1668968133/71707/7609fe79/598d0a1cN6029c147.jpg!q90.webp",
            "rank":1,
            "text":"美的（Midea）M1-L213C 快捷微波炉 微电脑操控 360°转盘加热 智能蒸煮菜单 21升",
            },
            {
              "img":"https://img11.360buyimg.com/mobilecms/s80x80_jfs/t3640/123/2611958810/256251/90e96dfe/5859d552N701e23c5.jpg!q90.webp",
              "rank":2,
              "text":"苏泊尔（SUPOR）电饭煲电饭锅4L容量微压力焖煮CFXB40FC829D-75（24小时预约）",
            },
            {
              "img":"https://img11.360buyimg.com/mobilecms/s80x80_jfs/t3211/104/550283976/137565/bbe9951a/57ba6c9aN0c6be511.jpg!q90.webp",
              "rank":3,
              "text":"美的（Midea）M1-L213B 快捷微波炉 360°转盘加热 旋钮操控 精准控温 五档火力 21升",
            },
          ],
          [
            {
            "img":"https://img30.360buyimg.com/mobilecms/s80x80_jfs/t17998/129/561011968/274584/275e6258/5a977599N86ade5b5.jpg!q90.webp",
            "rank":4,
            "text":"九阳（Joyoung）电磁炉整版触摸21HEC05赠汤锅+炒锅+刀具套装",
            },
            {
              "img":"https://img13.360buyimg.com/mobilecms/s80x80_jfs/t3178/23/9515163676/320811/fe2d86e9/58d5c6a8N0849687e.jpg!q90.webp",
              "rank":5,
              "text":"小熊（Bear）养生壶全自动玻璃加厚电热水壶花茶壶煮茶器黑茶煮茶壶多功能 YSH-A15W6 1.5L",
            },
            {
              "img":"https://img13.360buyimg.com/mobilecms/s80x80_jfs/t13756/85/469298344/238473/29c1ad5/5a0c0e5cN4cd96a9b.jpg!q90.webp",
              "rank":6,
              "text":"美的（Midea）电火锅MC-LHN30A家用多功能6L电煮锅电热锅电炒锅 双环聚能加热",
            },
          ]
        ],
        [
          [
            {
              "img":"//img20.360buyimg.com/mobilecms/s160x160_jfs/t8107/37/1359438185/72159/a6129e26/59b857f8N977f476c.jpg!q90.webp",
              "rank":1,
              "text":"Apple iPhone 8 Plus (A1864) 64GB 深空灰色 移动联通电信4G手机",
            },
            {
              "img":"//img20.360buyimg.com/mobilecms/s160x160_jfs/t12730/306/1517709913/155178/f5e7e927/5a22acfaNf7222715.jpg!q90.webp",
              "rank":2,
              "text":"一加手机5T 8GB+128GB 星辰黑 全面屏双摄游戏手机 全网通4G 双卡双待",
            },
            {
              "img":"//img20.360buyimg.com/mobilecms/s160x160_jfs/t12016/100/1221314692/239632/8b94bbc6/5a1d1d97Nf3afa7bb.jpg!q90.webp",
              "rank":3,
              "text":"荣耀 V10全网通 标配版 4GB+64GB 幻夜黑 移动联通电信4G全面屏手机 双卡双待",
            },
          ],
          [
            {
              "img":"//img13.360buyimg.com/mobilecms/s160x160_jfs/t3301/16/1615084619/137077/bc52150e/57d0c513Nd51ff9a3.jpg!q90.webp",
              "rank":4,
              "text":"Apple iPhone 7 (A1660) 128G 玫瑰金色 移动联通电信4G手机",
            },
            {
              "img":"//img20.360buyimg.com/mobilecms/s160x160_jfs/t15595/286/150857533/309262/39215dc0/5a28b5c6Ndec5088f.jpg!q90.webp",
              "rank":5,
              "text":"小米 红米5 Plus 全面屏手机 全网通版 3GB+32GB 金色 移动联通电信4G手机 双卡双待",
            },
            {
              "img":"//img20.360buyimg.com/mobilecms/s160x160_jfs/t8161/224/1169699991/177635/eb2192c2/59b64641N088dd6ad.jpg!q90.webp",
              "rank":6,
              "text":"小米Note3 美颜双摄拍照手机 6GB+64GB 黑色 全网通4G手机 双卡双待 ",
            },
          ]
        ],
        [
          [
            {
              "img":"//img30.360buyimg.com/mobilecms/s160x160_jfs/t14467/72/2386802546/219287/a152621e/5a98eb46N63f84897.jpg!q90.webp",
              "rank":1,
              "text":"小米（MI）电视 40英寸 智能WiFi网络平板 智能语音 电视机 标准版（黑）4A  L40M5-AD",
            },
            {
              "img":"//img14.360buyimg.com/mobilecms/s160x160_jfs/t13414/332/2604283059/358879/7a4380dc/5a4449c1Nee2e1dfe.jpg!q90.webp",
              "rank":2,
              "text":"康佳（KONKA）LED24E330C 24英寸高清窄边液晶平板电视 支持显示器(黑色)",
            },
            {
              "img":"//img20.360buyimg.com/mobilecms/s160x160_jfs/t13369/31/1697382897/132186/9871ed11/5a2601eeNf063c120.jpg!q90.webp",
              "rank":3,
              "text":"海尔（Haier)9公斤变频静音滚筒洗衣机 智能APP操控 双喷淋告别泡沫残留 EG9012B19SU1JD",
            },
          ],
          [
            {
              "img":"//img12.360buyimg.com/mobilecms/s160x160_jfs/t15583/141/2026999303/75976/2b38e658/5a72e3c2N5a745489.jpg!q90.webp",
              "rank":4,
              "text":"美菱(MELING)551升0.1度精控变频双开门 风冷无霜 电脑控温 纤薄对开门冰箱 玫瑰金 BCD-551WPCX",
            },
            {
              "img":"//img13.360buyimg.com/mobilecms/s160x160_jfs/t3133/14/1568885205/215983/d5a5af0/57cfb628N297332ea.jpg!q90.webp",
              "rank":5,
              "text":"海尔（Haier)10公斤变频滚筒洗衣机 智能APP控制 ABT双喷淋  EG10014B39GU1 ",
            },
            {
              "img":"//img11.360buyimg.com/mobilecms/s160x160_jfs/t5869/260/5089648292/100415/d58fb061/5959f81bNa0177aee.jpg!q90.webp",
              "rank":6,
              "text":"海尔（Haier） 318升 商用冰箱 卧式大冷冻柜 冷藏冷冻转换柜 变温冷柜 冰柜 BC/BD-318HD",
            },
          ]
        ],
      ],
      twoPageContainerShow:0,
      twoPageTickets:[ 
          [
            {
              "img":"//img11.360buyimg.com/babel/s140x140_jfs/t16231/272/2227481099/21708/c3bd92b9/5a96583eNaa802523.jpg!q90!cc_70x70.webp",
              "value":20,
              "limit":500,
              "text":"全品类（除特殊商品）【14点限量抢】",
            },
            {
              "img":"//img11.360buyimg.com/babel/s140x140_jfs/t3637/275/652996370/280419/2a134044/58105e15N75fb0595.jpg!q90!cc_70x70.webp",
              "value":20,
              "limit":490,
              "text":"部分京东自营手机商品",
            },
            {
              "img":"//img11.360buyimg.com/babel/s140x140_jfs/t6160/282/2516695973/187895/78cb5a3/5963618aNf0cf1e13.jpg!q90!cc_70x70.webp",
              "value":5,
              "limit":110,
              "text":"自营牛奶类部分商品",
            },
          ],
          [
            {
              "img":"//img11.360buyimg.com/babel/s140x140_jfs/t3181/129/4040202/36427/7b68fc5a/579f23ccN5e22e48f.jpg!q90!cc_70x70.webp",
              "value":1500,
              "limit":10000,
              "text":"【自营】冰箱洗衣机冷柜酒柜部分商品",
            },
            {
              "img":"//img11.360buyimg.com/babel/s140x140_jfs/t9316/20/480043317/353054/90eb59b1/59a907d2Nff9e96c9.jpg!q90!cc_70x70.webp",
              "value":40,
              "limit":199,
              "text":"三枪官方旗舰店",
            },
            {
              "img":"//img14.360buyimg.com/babel/s140x140_jfs/t19096/271/607335831/32295/2762ba0a/5a98f87fN350aef9f.jpg!q90!cc_70x70.webp",
              "value":100,
              "limit":199,
              "text":"晾晒女王节199减100（晾晒类部分商品",
            },
          ]
        ],
    }
  },
  components:{
    ScrollerL,
    Navbar,
    ShortCutHeader,
    searchBar,
    TwoPageContainer,
    RankListHeader,
    Tabs,
    ScrollerS,
    TextBoard,
    TwoPageTickets,

  },
  methods: {
    changeTab (index) {
      this.twoPageContainerShow = index
    }
  }
  
}
</script>
<style lang="less" scoped>
  * {
    padding:0;
    margin:0;
    border:0;
    outline:none;
    font-family: "Microsoft YaHei", tahoma, arial, "Hiragino Sans GB", "\\5b8b体", sans-serif;
  }
  .viewPort {
    width:1200px;
    margin:0 auto;
    .navPart {
      width:100%;
      height:500px;
      position:relative;
    }
    .rankPart {
      width:100%;
      margin-top:50px;
      height:450px;
      position:relative;
      .rankList,
      .vipAlbum,
      .tickets
       {
        display:inline-block;
        width:30%;
        height:100%;
        margin-right:20px;
      }
      .vipAlbum,
      .tickets {
        position: absolute;
        background:#fff;    
      }
      .tickets {
        right:60px;
      }
      
    }
  }
  
</style>
