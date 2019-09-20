<template>
  <div class="yn-gw-index-wrap">
    <div class="yn-official-website">

      <!-- 头部 -->
      <div class="yn-head-part">
        
        <!-- 顶部导航 -->
        <div class="yn-navigation-bar-part">
          <div class="navigation-bar-wrap">
            <!-- 公司logo -->
            <div class="navbar-logo">
              <img class="bar-logo-img" src="../assets/images/gw_logo.png" alt="">
              <!-- <div class="bar-logo-txt"></div> -->
            </div>
            <!-- 操作区 -->
            <div class="navbar-operation">
              <ul>
                <li><a href="#">优势</a>
                  <ul>
                    <li>测试</li>
                    <li>测试</li>
                    <li>测试</li>
                  </ul>
                </li>
                <li><a href="#">演示</a></li>
                <li><a href="#">展示</a></li>
                <li><a href="#">案例</a></li>
                <li><a href="#">关于我们</a></li>
                <li><a href="#">服务</a></li>
                <li><a href="#">合作伙伴</a></li>
              </ul>
            </div>
          </div>
        </div>
        <!-- 导航栏遮罩 -->
        <div class="yn-navigation-bg1" v-show="isNavigationbg" :class="navani"></div>
        <div class="yn-navigation-bg2" v-show="isNavigationbg" :class="navani"></div>

        <!-- 轮播图 -->
        <div class="yn-banner-part">
          <el-carousel @change="changeBanner" :height="banner_height">
            <el-carousel-item v-for="(item ,index)  in banner_list" :key="index">
              <div class="yn-banner-content"
                  :class="[banner_bgcolor]" 
                  :style="{height:banner_height}">
                <!-- 轮播介绍部分 -->
                <div class="banner-introduce" :class="bainani">
                  <!-- <div>物联网+农业大数据</div>
                  <div>推动农业智能化和现代化</div>
                  <div>易农智慧农业云平台</div>
                  <div>强势上线</div> -->
                  <div>{{item.context_one}}</div>
                  <div>{{item.context_two}}</div>
                  <div>{{item.context_three}}</div>
                  <div>{{item.context_four}}</div>
                  <div>
                    <div>{{item.context_fift}}</div>
                    <div class="mark"></div>
                  </div>
                </div>
                <!-- 轮播图片部分 -->
                <div class="banner-picture">
                  <img :src="banner_src" alt="">
                </div>
              </div>
            </el-carousel-item>
          </el-carousel>
        </div>

        <!-- 返回顶部 -->
        <div class="yn-return-top-wrap" v-show="isNavigationbg">
          <div class="return-top-btn" @click="return_top">
            <img src="../assets/images/topbtn.png" alt="">
          </div>
        </div>

        <!-- 侧边导航 -->
        <div class="yn-side-navigation-wrap" v-show="isNavigationbg">
          <!-- 导航按钮 -->
          <div class="side-navigation-part" v-show="isSideNavigation">
            <div class="leav-message-btn" @click="show_message()">
              <div>
                <img src="../assets/images/message.png" alt="">
              </div>
            </div>
          </div>
          <!-- 点击显示内容 -->
          <div class="side-leav-message-part" v-show="isSideMessage" :class="slmpani">
            <div class="title-strip">
              <div>留言板</div>
              <div @click="fade_message()">—</div>
            </div>
            <div class="content-input">
              <el-input v-model="message_form.side_name" placeholder="姓名"></el-input>
              <el-input v-model="message_form.side_email" placeholder="邮箱"></el-input>
              <el-input v-model="message_form.side_email" placeholder="电话"></el-input>
              <el-input
                type="textarea"
                :rows="3"
                resize='none'
                placeholder="请输入留言内容"
                v-model="message_form.side_content">
              </el-input>
              <el-button type="primary">提交</el-button>
            </div>
          </div>
        </div>
      </div>

      <!-- 内容部分 -->
      <div class="yn-content-part">

        <!-- 我们的优势部分 -->
        <div class="yn-advantage-wrap">
          <div class="round-decorate"></div>
          <div class='round-decorate-rocket'>
            <img src="../assets/images/rocket.png" alt="">
          </div>
          <!-- 优势标题 -->
          <div class="yn-advantage-title">
            <div class="title">从创办至今我们还在坚持</div>
            <div class="advantage-title-pic">
              <img src="../assets/images/line.png" alt="">
            </div>
          </div>
          <!-- 优势内容 -->
          <div class="yn-advantage-content">
            <div class="advantage-piece" 
              :class="advani"
              v-for="(item,index) of advantage_list">
              <div class="piece-substance">
                <span class="dot one"></span>
                <span class="dot two"></span>
                <span class="dot three"></span>
                <div class="advantage-piece-pic">
                  <img :src="item.pic_src">
                </div>
                <div class="advantage-piece-title">
                  {{item.title}}
                </div>
                <div class="advantage-piece-introduce">
                  {{item.content}}
                </div>
              </div>        
            </div>   
          </div>
        </div>

        <!-- 项目示例部分 -->
        <div class="yn-project-example-wrap">
          <div class="yn-project-example-content">
            <!-- 视频 -->
            <div class="yn-project-example-video example-piece" :class="exani">
                <video muted width="600" height="450" autoplay loop>
                      <source src="../assets/images/testvideo.mp4"  type="video/mp4" >
                      您的浏览器不支持 video 标签
                </video>
            </div>
            <!-- 介绍 -->
            <div class="yn-project-example-info example-piece" :class="exani">
              <div class="project-content">
                <div>农业物联网监控系统</div>
                <div>
                  <div class="digital-statistic">
                    <span>24</span>
                    <span>小时</span>
                    <p>全天候监控</p>
                  </div>
                  <div class="digital-statistic">
                    <span>1440</span>
                    <span>分钟</span>
                    <p>实时数据采集</p>
                  </div>
                </div>
                <div class="sensor-info-show">
                  <div class="sensor-info-content">
                    <div class="sensor-info" v-for="(items , index) of sensor_infoList">
                      <div class="sensor-info-pic">
                        <img :src="items.pic_src" alt="">
                      </div>
                      <div class="sensor-info-txt">
                        <span>{{items.title}}</span>
                        <span>{{items.data}}</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- 产品展示 -->
        <div class="yn-product-exhibition-wrap" :style="{height:product_height}">
          <div class="product-exhibition-content">
            <div class="product-exhibition">
              <div class="product-pic">
                <img src="../assets/images/view.png" alt="">
              </div>
              <div class="product-title">气象监测站</div>
              <div class="product-content">
                <span>便携式</span>
                <span>太阳能</span>
                <span>农田小气候无线实时观测站</span>
                <p>农业种植、养殖、公园、厂区、园区的小气候环境监测专家</p>
              </div>
              <div class="product-introduce">农业水产养殖水环境监测存在环境苛刻，水质变化剧烈,数据的实时性要求高；人为干扰严重，检测难度大，我司开发的浮台型水环境监测站成功解决这些问题。</div>
              <div class="product-more-btn">了解详情 →</div>
            </div>
          </div>
          <div class="product-exhibition-content">
            <div class="product-exhibition">
              <div class="product-pic">
                <img src="../assets/images/yxft.png" alt="">
              </div>
              <div class="product-title">水质监测站</div>
              <div class="product-content">
                <span>浮台型</span>
                <span>太阳能</span>
                <span>水环境无线实时监测站</span>
                <p>水环境监测专家</p>
              </div>
              <div class="product-introduce">农业水产养殖水环境监测存在环境苛刻，水质变化剧烈,数据的实时性要求高；人为干扰严重，检测难度大，我司开发的浮台型水环境监测站成功解决这些问题。</div>
              <div class="product-more-btn">了解详情 →</div>
            </div>
          </div>
          <div class="product-exhibition-content">
            <div class="product-exhibition">
              <div class="product-pic">
                <img src="../assets/images/wxdhycgq.png" alt="">
              </div>
              <div class="product-title">无线多合一传感器</div>
              <div class="product-content">
                <span>无线</span>
                <span>太阳能</span>
                <span>多合一传感器</span>
                <p>农业生产环境、气象、水文、景区环境监测专家</p>
              </div>
              <div class="product-introduce">无线多合一传感器是我司在物联网监测方面积累多年行业经验的结晶。</div>
              <div class="product-more-btn">了解详情 →</div>
            </div>
          </div>
        </div>

        <!-- 成功案例 -->
        <!-- <div class="yn-success-example-wrap">
          <div class="yn-success-example-container">
            <div class="yn-success-example-title">
              <div>想要和像他们一样成功？</div>
              <div>所有的困难都帮你过滤</div>
            </div>
            <div class="yn-success-example-content">
              <div class="success-example-piece">
                <div class="example-case-content">
                  <div class="example-case-title">
                    <div>生态牦牛养殖</div>
                    <div>甘孜州色达县生态牦牛养殖，位于川西高原，占地100亩。克服高海拔，低气温。打造全新的物联网智慧生态养殖基地。</div>
                  </div>
                  <div class="example-case-btn">
                    <div>了解更多</div>
                  </div>
                </div>
              </div>

              <div class="success-example-piece">
                <div class="example-case-content">
                  <div class="example-case-title">
                    <div>生态牦牛养殖</div>
                    <div>甘孜州色达县生态牦牛养殖，位于川西高原，占地100亩。克服高海拔，低气温。打造全新的物联网智慧生态养殖基地。</div>
                  </div>
                  <div class="example-case-btn">
                    <div>了解更多</div>
                  </div>
                </div>
              </div>

              <div class="success-example-piece">
                <div class="example-case-content">
                  <div class="example-case-title">
                    <div>生态牦牛养殖</div>
                    <div>甘孜州色达县生态牦牛养殖，位于川西高原，占地100亩。克服高海拔，低气温。打造全新的物联网智慧生态养殖基地。</div>
                  </div>
                  <div class="example-case-btn">
                    <div>了解更多</div>
                  </div>
                </div>
              </div>

              <div class="success-example-piece">
                <div class="example-case-content">
                  <div class="example-case-title">
                    <div>生态牦牛养殖</div>
                    <div>甘孜州色达县生态牦牛养殖，位于川西高原，占地100亩。克服高海拔，低气温。打造全新的物联网智慧生态养殖基地。</div>
                  </div>
                  <div class="example-case-btn">
                    <div>了解更多</div>
                  </div>
                </div>
              </div>
            </div>
            <div class="yn-more-success-btn">
              <el-button type="primary" plain>更多成功案例</el-button>
            </div>
          </div> 
        </div> -->

        <!-- 关于我们 -->
        <div class="yn-about-company-wrap">
          <div class="yn-about-company-container" :class="abcani">
            <div>
              <img src="../assets/images/gsxx.jpg" alt="">
            </div>
            <div>
              <div class="about-company-title">关于我们</div>
              <div class="about-company-introduce">成都市易农科技</div>
              <div class="about-company-content">专注于智慧农业领域的高科技公司。公司致力于利用物联网、人工智能、大数据、区块链技术服务现代农业；推动中国农业走向：生产集约化、管理信息化、决策智能化、销售互联网化、农产品质量可全程溯源化。经过多年发展，公司业务拓展到四川、重庆、贵州、云南、甘肃、陕西等地。具体业务涵盖各细分龙头公司的生产环节、流通环节和销售环节。公司开发的相关产品有效帮助这些企业：提升了生产管理水平、实现了决策管理的智能化，拓展了销售渠道，取得良好的经济效益。</div>
              <div class="about-company-details">了解更多→</div>
            </div>
          </div>
        </div>

        <!-- 我们的服务 -->
        <div class="yn-company-service-wrap">
          <div class="yn-company-service-container">
            <!-- 我们的服务标题 -->
            <div class="yn-company-service-title">
              <div>我们的服务，永远不会迟到</div>
              <div>你的最佳选择</div>
            </div>
            <!-- 循环展示内容 -->
            <div class="yn-company-service-content" :class="comsani">
              <div class="company-service-piece" 
              v-for="(item,index) of service_list"
              :style="{backgroundImage: 'url(' + item.pic_src + ')' }"
              >
                <div class="mask"></div>
                <div class="company-service-content">
                  <div class="company-service-title">
                    <div>{{item.title}}</div>
                    <div>{{item.content}}</div>
                  </div>
                  <div class="company-service-btn">
                    <el-button type="primary">了解更多</el-button>
                  </div>
                </div>
              </div>
            </div>
          </div> 
        </div>

        <!-- 成功客户案例 -->
        <div class="yn-customer-case-wrap" :style="{height:HEIGHT+'px'}">
          <div class="yn-customer-case-container">
            <div class="yn-success-example-title">
              <div>想要和像他们一样成功？</div>
              <div>所有的困难都帮你过滤</div>
            </div>
            <!-- 滚动循环 -->
            <el-carousel @change="changeBanner" :height="HEIGHT-150+'px'" :autoplay="false">
              <el-carousel-item 
                v-for="(banner_item ,banner_index)  in customercase_banner_list" 
                :key="banner_index"
                >
                <!-- 内容循环 -->
                <div class="customer-case-banner" :class="cuscani">

                  <div class="customer-case-piece" 
                    v-for="(piece_item,piece_index) in banner_item.customer_caseList" 
                    :key="piece_index"
                    >

                    <div class="customer-case-title">
                      <div>{{piece_item.title}}</div>
                      <div>了解更多→</div>
                    </div>

                    <div class="customer-case-introduce">{{piece_item.introduction}}</div>

                    <!-- 成功基地条数循环 -->
                    <div class="customer-case-list">
                      <div class="customer-case-content" 
                      v-for="(content_item,content_index) in piece_item.single_list"
                      :key="content_index">

                        <div>
                          <img :src="content_item.pic_src">
                        </div>

                        <div>
                          <div>{{content_item.title}}</div>
                          <div>→</div>
                        </div>

                      </div>
                    </div>
                  </div>
                </div>
              </el-carousel-item>
            </el-carousel>
          </div>
        </div>

        <!-- 我们的合作商 -->
        <div class="yn-cooperative-partner-wrap">
          <div class="cooperative-partner-title">
            <div>我们的合作商</div>
          </div>
          <div class="cooperative-partner-content">
            <div class="cooperative-partner-list"
            v-for="(itme,index) of partner_list">
              <div class="cooperative-partner-piece">
                <div class="cooperative-pic">
                  <img :src="itme.partner_src"></img>
                </div>
              </div>
            </div>
            
          </div>
        </div>
      </div>

      <!-- 底部 -->
      <div class="yn-foot-part">
        <div class="yn-foot-information-wrap">
          <div class="yn-foot-information-content">
            <div class="foot-information">
              <div>关于</div>
              <div>
                <a href="">公司概况</a>
                <a href="">发展历程</a>
                <a href="">研发团队</a>
                <a href="">公司理念</a>
                <a href="">公司招聘</a>
              </div>
            </div>
            <div class="foot-information">
              <div>服务</div>
              <div>
                <a href="">智慧农业云平台</a>
                <a href="">垃圾分类平台</a>
                <a href="">生产管理平台</a>
                <a href="">溯源平台</a>
                <a href="">更多服务</a>
              </div>
            </div>
            <div class="foot-information">
              <div>产品</div>
              <div>
                <a href="">太阳能气象站</a>
                <a href="">太阳能墒情站</a>
                <a href="">水质监测站</a>
                <a href="">传感器</a>
                <a href="">更多产品</a>
              </div>
            </div>
            <div class="foot-information">
              <div>联系我们</div>
              <div>
                <a href="">电话</a>
                <a href="">邮箱</a>
                <a href="">留言</a>
                <a href="">地址</a>
                <a href="">更多</a>
              </div>
            </div>
          </div>
        </div>
        <div class="yn-trademark-wrap">
          © 2019 成都市易农科技有限公司。
          蜀ICP备16005725号
        </div>
      </div>

    </div>
  </div>
</template>






<script>
import '../assets/css/common.css'
import '../assets/css/index.scss' 
import { setTimeout } from 'timers';
export default {
  data(){
    return{
      isNavigationbg:false,//导航条遮罩层
      isSideMessage:false,//是否显示留言板
      isSideNavigation:true,//是否显示侧边导航
      HEIGHT:'',//屏幕高度
      WIDTH:'',//屏幕宽度
      banner_height:'',//轮播图高度
      product_height:'',//我们的产品高度
      navani:'',//导航条动画
      bainani:'',//轮播图的动画
      slmpani:'',//留言板的动画
      advani:'',//优势的动画
      exani:'',//随机示例动画
      abcani:'',//关于我们动画
      comsani:'',//我们的服务动画
      cuscani:'',//客户案例动画
      isAdvAni:true,//是否要显示（优势）动画
      isExaAni:true,//是否要显示（随机示例）动画
      isAbcAni:true,//是否要显示（关于我们）动画
      isComsAni:true,//是否要显示（我们的服务）动画
      isCuscAni:true,//是否要显示（客户案例）动画
      //留言板
      message_form:{
        side_name:'',
        side_email:'',
        side_content:''
      },
      //轮播图列表
      banner_list:[
        {
          context_one:'物联网+农业大数据',
          context_two:'推动农业智能化和现代化',
          context_three:'易农智慧农业云平台',
          context_four:'强势上线',
          context_fift:'了解详情',
          banner_bgcolor:'banner-blue',//轮播图背景颜色
          banner_src:require('../assets/images/yn-cloud.png')//轮播图图片
        },
        {
          context_one:'践行新发展理念+推动可持续发展',
          context_two:'青山绿水就是金山银山',
          context_three:'垃圾分类智慧平台',
          context_four:'即将上线',
          context_fift:'了解详情',
          banner_bgcolor:'banner-green',//轮播图背景颜色
          banner_src:require('../assets/images/yn-cloud-1.png')//轮播图图片
        }
      ],
      banner_bgcolor:'banner-blue',//轮播图背景颜色
      banner_src:require('../assets/images/yn-cloud.png'),//轮播图图片
      //我们的优势列表
      advantage_list:[
        {
          pic_src:require('../assets/images/strength.png'),
          title:'最强实力',
          content:'我们凭借雄厚的经济实力、先进的技术、可靠的质量、科学的管理、完善的服务和务实、创新的精神，在做大、做实、做强企业。'
        },
        {
          pic_src:require('../assets/images/iot.png'),
          title:'物联网',
          content:'以实现智能化识别、定位、跟踪、监管等功能。我们旗下的智慧农业云平台和垃圾分类智慧平台引领万物互联。'
        },
        {
          pic_src:require('../assets/images/famer.png'),
          title:'专注农业',
          content:'易农科技致力于将互联网+农业、农业物联网、人工智能大数据技术与农业生产经营相结合,为用户提供业界领先的智慧农业解决方案,促进农产品安全与品质的提升。'
        },
        {
          pic_src:require('../assets/images/famer.png'),
          title:'专注农业',
          content:'易农科技致力于将互联网+农业、农业物联网、人工智能大数据技术与农业生产经营相结合,为用户提供业界领先的智慧农业解决方案,促进农产品安全与品质的提升。'
        },
      ],
      //项目实例的传感器数据列表
      sensor_infoList:[
        {
          pic_src:require('../assets/images/jyl.png'),
          title:'雨量',
          data:'5mm'
        },
        {
          pic_src:require('../assets/images/trwd.png'),
          title:'土壤温度',
          data:'25℃'
        },
        {
          pic_src:require('../assets/images/gz.png'),
          title:'光照',
          data:'150516Lux/Lx'
        },
        {
          pic_src:require('../assets/images/dqy.png'),
          title:'大气压',
          data:'960Lux/Lx'
        },
        {
          pic_src:require('../assets/images/zjs.png'),
          title:'重金属',
          data:'150g/kg'
        },
        {
          pic_src:require('../assets/images/sd.png'),
          title:'空气湿度',
          data:'61.5%RH'
        }
      ],
      //我们的服务列表
      service_list:[
        {
          title:'物联网',
          content:'全新版本易农智慧农业云平台2.0为您提供服务',
          pic_src:require('../assets/images/service-iot.jpg'),
        },
        {
          title:'生产管理',
          content:'办公室轻松管理，玩手机也能管理',
          pic_src:require('../assets/images/service-scgl.jpg'),
        },
        {
          title:'溯源系统',
          content:'农产品全知道，健不健康尽收眼底',
          pic_src:require('../assets/images/service-syxt1.jpg'),
        }
      ],
      //客户成功案例轮播列表
      customercase_banner_list:[
        {
          //分地区列表
          customer_caseList:[
            {
              title:'四川物联网产业园',
              introduction:'四川省原有面积57万平方公里，人口1．1亿多，在全国具有举足轻重的地位，农业占全国的比重很大。1997年，调整行政区，重庆市升为直辖市，涪陵、万县和黔江三个地区划归重庆市，四川的面积减少近9万平方公里，人口减少3 000多万，农业占全国的比重也随之下降。全省的人口、粮食产量从全国的第一位下降至三、四位。',
              //单个案例列表
              single_list:[
                {
                  pic_src:require('../assets/images/mnyz.jpg'),
                  title:'色达县生态牦牛养殖。克服高海拔，低气温。打造全新的物联网智慧生态养殖基地。',
                },
                {
                  pic_src:require('../assets/images/dxgz.jpg'),
                  title:'智慧稻虾共作,与四川中伦信息发展有限公司合作',
                },
                {
                  pic_src:require('../assets/images/jpsgsc.jpg'),
                  title:'精品水果生产',
                },
                {
                  pic_src:require('../assets/images/tjzzxxh.jpg'),
                  title:'藤椒种植信息化',
                }
              ]
            },
            {
              title:'重庆物联网产业园',
              introduction:'市域植物资源丰富，生长6000多种各类植物，森林覆盖率39％。重庆药用植物资源极其丰富，是全国重要的中药材产地之一，大面积山区生长的野生和人工培植的中药材有2000余种，主要有黄连、白术、金银花、党参、贝母、天麻、厚朴、黄桕、杜仲、元胡、当归等。石柱土家族自治县黄连产量居全国第一，是著名的"黄连之乡"。',
              //单个案例列表
              single_list:[
                {
                  pic_src:require('../assets/images/mnyz.jpg'),
                  title:'川蒲生态柑橘',
                },
                {
                  pic_src:require('../assets/images/dxgz.jpg'),
                  title:'肖敏生态鱼养殖',
                },
                {
                  pic_src:require('../assets/images/mnyz.jpg'),
                  title:'开州柑橘物联网',
                },
                {
                  pic_src:require('../assets/images/mnyz.jpg'),
                  title:'生态农业示范园',
                }
              ]
            },
          ],
        },
        {
          customer_caseList:[
            {
              title:'贵州物联网产业园',
              introduction:'在农业和农村经济建设中依靠科技进步，坚持经济发展与生态建设的辩证统一是确保农业可持续发展的一条不可逾越的基本原则。但是近年来，贵州生态农业建设取得一些成绩和经验，实现了粮食增产、农业增效、农民增收。',
              //单个案例列表
              single_list:[
                {
                  pic_src:require('../assets/images/mnyz.jpg'),
                  title:'色达县生态牦牛养殖。克服高海拔，低气温。打造全新的物联网智慧生态养殖基地。',
                },
                {
                  pic_src:require('../assets/images/dxgz.jpg'),
                  title:'智慧稻虾共作,与四川中伦信息发展有限公司合作',
                },
                {
                  pic_src:require('../assets/images/jpsgsc.jpg'),
                  title:'精品水果生产',
                },
                {
                  pic_src:require('../assets/images/tjzzxxh.jpg'),
                  title:'藤椒种植信息化',
                }
              ]
            }
          ]
        }
      ],
      //我们的合作商
      partner_list:[
        {
          partner_src:require('../assets/images/scnykxy.png'),//合作商图片
        },
        {
          partner_src:require('../assets/images/xzjt.png'),
        },
        {
          partner_src:require('../assets/images/bxsc.jpg'),
        },
        {
          partner_src:require('../assets/images/cdnlxy.jpg'),
        }
      ],
    }
  },
  mounted(){
    //屏幕高度
    this.HEIGHT=window.innerHeight || document.documentElement.clientHeight || document.body.clientHeight
    this.WIDTH=window.innerWidth || document.documentElement.clientWidth || document.body.clientWidth
    //监听滚动
    window.addEventListener('scroll', this.handleScroll);
    //初始化
    this.init();
  },
  methods:{
    //初始化
    init(){
      console.log(this.HEIGHT)
      if(this.HEIGHT>776){
        //banner高度
        this.banner_height=this.HEIGHT/1.5+'px';
        //产品区域高度
        this.product_height='776px';
        setTimeout(()=>{
          this.advani='advantage-ani';
          this.isAdvAni=false;
        },50);
      }
      else{
        //banner高度
        this.banner_height=this.HEIGHT+'px';
        //产品区域高度
        this.product_height=this.HEIGHT+'px';
      }
      //banner动画
      setTimeout(()=>{
        this.bainani='banner-introduce-ani';
      },50);
    },
    handleScroll () {
      var scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop
      console.log(scrollTop)
      //监听导航栏
      if(scrollTop===0){
        this.isNavigationbg=false;
        setTimeout(()=>{
          this.navani=''
        },50)  
        console.log(this.navani)
      }
      else{
        this.isNavigationbg=true;
        setTimeout(()=>{
          this.navani='navigation-ani'
        },50)  
      } 
      //监听我们的优势
      if(this.isAdvAni){
        let advantage_dom = document.querySelector(".piece-substance");
        if(this.HEIGHT+scrollTop>advantage_dom.offsetTop){
          console.log('我们的优势动画加载');
          setTimeout(()=>{
            this.advani='advantage-ani';
            this.isAdvAni=false;
          },50)  
        }
      }
      //监听随机示例
      if(this.isExaAni){
        let example_dom = document.querySelector(".yn-project-example-content");
        if(this.HEIGHT+scrollTop>example_dom.offsetTop){
          console.log('随机示例动画加载');
          setTimeout(()=>{
            this.exani='example-ani';
            this.isExaAni=false;
          },50)  
        }
      }
      //监听关于我们
      if(this.isAbcAni){
        let about_dom = document.querySelector(".yn-about-company-container");
        if(this.HEIGHT+scrollTop>about_dom.offsetTop+150){
          console.log(about_dom.offsetTop);
          console.log('关于我们动画加载');
          setTimeout(()=>{
            this.abcani='about-company-ani';
            this.isAbcAni=false;
          },50)  
        }
      }
      //监听我们的服务
      if(this.isComsAni){
        let service_dom = document.querySelector(".yn-company-service-content");
        if(this.HEIGHT+scrollTop>service_dom.offsetTop){
          console.log(service_dom.offsetTop);
          console.log('我们的服务动画加载');
          setTimeout(()=>{
            this.comsani='company-service-ani';
            this.isComsAni=false;
          },50)  
        }
      }
      //监听用户案例
      if(this.isCuscAni){
        let customer_dom = document.querySelector(".yn-customer-case-container");
        if(this.HEIGHT+scrollTop>customer_dom.offsetTop){
          console.log(customer_dom.offsetTop);
          console.log('用户案例动画加载');
          setTimeout(()=>{
            this.cuscani='customer-case-ani';
            this.isCuscAni=false;
          },50)  
        }
      }
    },
    //监听轮播图切换的时候
    changeBanner(v){
      if(v==0){
        this.banner_bgcolor='banner-blue';
        this.banner_src=require('../assets/images/yn-cloud.png');
      }
      if(v==1){this.banner_bgcolor='banner-green';this.banner_src=require('../assets/images/yn-cloud-1.png');}
    },
    //显示留言板
    show_message(){
      setTimeout(()=>{
        this.slmpani='leav-message-ani';
      },50) 
      this.isSideMessage=true;
      this.isSideNavigation=false;
    },
    //隐藏留言板
    fade_message(){
      this.slmpani='';
      setTimeout(()=>{
        this.isSideMessage=false;
        this.isSideNavigation=true;
      },100) 
      
    },
    //返回顶部
    return_top(){
      console.log("a")
      let nowTop = document.body.scrollTop || document.documentElement.scrollTop; // 获取当前滚动条位置
      if (nowTop > 0) {
          window.requestAnimationFrame(this.return_top);
          window.scrollTo (0,nowTop - (nowTop/5));
      }
    }
  },
  //移除滚动监听
  destroyed(){
    window.removeEventListener('scroll', this.handleScroll);
  }
};
</script>

<style> 
   /*轮播图指示器  */
  .el-carousel__button{
    height: 10px !important;
  }
</style>
