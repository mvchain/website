<template>
  <div id="homeCon" @scroll="divScroll" class="home">
    <el-row :gutter="10"  class="home-logo" >
      <el-col :xs="0"></el-col>
      <el-col  class="home-head" :xs="0" :class="isNag ? 'home-head-show': ''">
        <div>
          <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/title-logo.png" alt="mvc">
          <img v-show="false" style="width:121px;height:75px" src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/title-logo.png" alt="小牛链 mvc 官网 logo">
        </div>
        <div class="home-navigation">
          <div class="home-navigation1">
            <div class="home-navigation-item" v-for="(v, k) in navigationList" :key="k">
              <a target="_blank" :href="v.target" :class="k === targetKey ? 'active' : ''">{{langFlag?v.zn:v.en}}</a>
            </div>
          </div>

        </div>
        <div class="lan-tab">
          <!--<span @click="tabLan(true)">中</span>-->
          <!--<span>|</span>-->
          <span @click="tabLan(false)">EN</span>
        </div>
      </el-col>
      <el-col :xs="0" id="homePage">
        <el-carousel class="banner-div" height="40vw">
          <el-carousel-item class="banner-div" v-for="(v, k) in bannerList" :key="k">
            <div class="banner-div-item" @click="changePage(k)">
              <img :src="v.src">
            </div>
          </el-carousel-item>
        </el-carousel>

      </el-col>
    </el-row>
    <el-row class="home-content" :gutter="10">
      <el-col :xs="0">
        <div class="trading-platform" id="tradingPlatform">
          <div>
            <div  class="trading-platform-con">
              <div class="title-con">
                <p class="mvc-title">{{langFlag?langTxt.Zn[7]:langTxt.En[7]}}</p>
                <p class="mvc-title1">{{langFlag?langTxt.Zn[40]:langTxt.En[28]}}</p>
              </div>
              <div class="icon-item icon-line1">
                <a target="_blank" href="https://www.aoex.com/">
                  <img src="https://ico-list.oss-cn-hangzhou.aliyuncs.com/cryptovalut/20190402145147nQcAB6Gf5H.png" alt="">
                </a>
                <a target="_blank" href="https://dex.top/trade/ETH_MVC">
                  <img src="https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180728141326pNwYwQ8Z5t.png" alt="">
                </a>
                <a target="_blank" href="https://www.coinegg.com/btc/mvc/">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/coinegglogo.png" alt="">
                </a>
                <a target="_blank" href="https://transfer.swft.pro/swft-v3-en/swft-v3-en-pc/index.html">
                  <img src="https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180728142110zBBZeHsWdt.png" alt="">
                </a>


              </div>
              <div class="icon-item icon-line2">
                <a target="_blank" href="https://www.fubt.top/trade/cny_coin.html?tradeId=15&type=2">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/fubtlogo.png" alt="">
                </a>
                <a target="_blank" href="https://otcbtc.com/">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/otcbtc.png" alt="">
                </a>
                <a target="_blank" href="https://coin2co.in/exchange/C2C_MVC">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/coincoin.png" alt="">
                </a>
                <a target="_blank" href="https://www.oex.com/trade/cny_coin.html?tradeId=39&type=2">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/oexlogo.png" alt="">
                </a>


              </div>
              <div class="icon-item icon-line3">
                <a target="_blank" href="https://yobit.net/en/trade/MVC/BTC">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/yobitlogo.png" alt="">
                </a>
                <a target="_blank" href="https://www.uncoinex.com">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/u-coinlogo.png" alt="">
                </a>
                <a target="_blank" href="https://www.kex.com/trade/cny_coin.html?tradeId=42&type=4">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/kexlogo.png" alt="">
                </a>
                <a target="_blank" href="https://www.rightbtc.com">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/hftlogo.png" alt="">
                </a>

              </div>
              <div class="icon-item icon-line2">
                <a target="_blank" href="https://etherdelta.com/#MVC-ETH">
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/etherlogo.png" alt="">
                </a>
                <a href="" style="opacity: 0"></a><a href="" style="opacity: 0"></a><a href="" style="opacity: 0"></a>
              </div>
            </div>
          </div>
          <div class="introduction" id="introduction">
            <div class="title-con" style="margin-top:150px;">
              <p class="mvc-title">{{langFlag?langTxt.Zn[8]:langTxt.En[8]}}</p>
            </div>
            <div class="introduction-content">
              <div class="introduction-content-item">
                <div class="introduction-content-item-num">01</div>
                <div class="introduction-content-item-title">{{langFlag?langTxt.Zn[9]:langTxt.En[9]}}</div>
                <div class="introduction-content-item-content">{{langFlag?langTxt.Zn[12]:langTxt.En[12]}}</div>
              </div>
              <div class="introduction-content-item">
                <div class="introduction-content-item-num">02</div>
                <div class="introduction-content-item-title">{{langFlag?langTxt.Zn[10]:langTxt.En[10]}}</div>
                <div class="introduction-content-item-content">{{langFlag?langTxt.Zn[13]:langTxt.En[13]}}</div>
              </div>
              <div class="introduction-content-item" >
                <div class="introduction-content-item-num">03</div>
                <div class="introduction-content-item-title">{{langFlag?langTxt.Zn[11]:langTxt.En[11]}}</div>
                <div class="introduction-content-item-content" >{{langFlag?langTxt.Zn[14]:langTxt.En[14]}}</div>
              </div>
            </div>
          </div>
          <div class="technology-x" id="technology">
            <div class="technology" style="margin-top:80px;">
              <div class="technology-head">
                <div class="technology-head-con">
                  <div>{{langFlag?langTxt.Zn[15]:langTxt.En[29]}}</div>
                  <div>{{langFlag?langTxt.Zn[41]:langTxt.En[30]}}</div>
                </div>
              </div>
              <div class="technology-content">
                <div class="technology-all">
                  <div>
                    <div class="introduction-content-item-num" style="background:#f04343;">01</div>
                    <div class="technology-content-top">
                      <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/lock.png" alt="">
                    </div>
                    <div class="technology-content-down">{{langFlag?langTxt.Zn[42]:langTxt.En[31]}}</div>
                  </div>
                  <div>
                    <div class="introduction-content-item-num" style="background:#f04343;">02</div>
                    <div class="technology-content-top">
                      <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/rocket.png" alt="">
                    </div>
                    <div class="technology-content-down">{{langFlag?langTxt.Zn[43]:langTxt.En[32]}}</div>
                  </div>
                  <div>
                    <div class="introduction-content-item-num" style="background:#f04343;">03</div>
                    <div class="technology-content-top">
                      <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/circle.png" alt="">
                    </div>
                    <div class="technology-content-down">{{langFlag?langTxt.Zn[44]:langTxt.En[33]}}</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div id="team" class="team">
           <!-- <div class="team-all">
              <div class="title-con" style="margin-top:100px;">
                <p style="position: relative;top:40px;" class="mvc-title">{{langFlag?langTxt.Zn[45]:langTxt.En[34]}}</p>
              </div>
              <div class="team-photo">
                <div v-for="(v, k) in photoSrc" :key="k.key">
                  <div class="photo-image"><img :src="v.src"></div>
                  <div class="photo-name">{{langFlag?v.znName:v.enName}}</div>
                  <div class="photo-position">{{langFlag?v.znPosition:v.enPosition}}</div>
                  <div class="photo-introduction">{{langFlag?v.znIntroduction:v.enIntroduction}}</div>
                </div>
              </div>
            </div>-->
          </div>
          <div class="partner" id="partner">
            <div class="title-con" style="margin-top:150px;">
              <p class="mvc-title" style="color:#000">{{langFlag?langTxt.Zn[46]:langTxt.En[42]}}</p>
            </div>
            <div class="partner-content">
              <div class="partner-content-item">
                <div>
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/7.png" alt="">
                </div>
                <div>
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/2.png" alt="">
                </div>
                <div>
                  <img  src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/3.png" alt="">
                </div>
                <div>
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/1.png" alt="">
                </div>
              </div>
              <div class="partner-content-item">

                <div>
                  <img  src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/13.png" alt="">
                </div>
                <div>
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/10.png" alt="">
                </div>
                <div>
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/11.png" alt="">
                </div>
                <div>
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/12.png" alt="">
                </div>
              </div>

              <div>
                <div>
                  <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/8.png" alt="">
                </div>
                <div>
                  &nbsp;
                </div>
                <div>
                  &nbsp;
                </div>
                <div>
                  &nbsp;
                </div>
              </div>
            </div>
          </div>
          <div class="home-foot">
            <el-row class="home-foot-con">
              <el-col :span="12" class="home-foot-top">
                <span class="foot-icon1"></span>
                <span style="font-size:16px; color:#fff;">mvc@MVChain.net</span>
              </el-col>
              <el-col :span="12"  class="home-foot-mid">
                <a href="https://twitter.com/MaverickChain"></a>
                <a href="https://github.com/mvchain"></a>
              </el-col>
              <el-col :span="24" class="home-foot-foot">
                <span  class="foot-icon2" style="font-size:24px;"></span>
                <span  style="font-size:16px;color:#fff;">Contract Address：0xb17df9a3b09583a9bdcf757d6367171476d4d8a3</span>
              </el-col>
            </el-row>
            <div class="home-foot-bottom">
              Maverick Chain is developed and operated by Geniusmobi Co.ltd, a company registrated in Republic of Seychelles.
            </div>
          </div>
        </div>
      </el-col>
    </el-row>
    <el-row class="m-home" :gutter="10">
      <div class="m-home-model">
        <transition name="el-fade-in-linear">
          <div v-show="modelFlag" class="transition-box">
            <div class="m-home-nag-logo">
              <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo-m.png" alt="logo">
              <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/close.png" alt="" @click="modelFlag = !modelFlag">
            </div>
            <div class="transition-box-content">
              <ul>
                <li v-for="(v, k) in navigationList" :key="k">
                  <a target="_blank" :href="v.mTarget" @click="getButton(k)" :class="k === targetKey ? 'active' : ''">{{langFlag?v.zn:v.en}}</a>
                </li>
              </ul>
            </div>
          </div>
        </transition>
      </div>
      <div class="m-home-content">
        <el-col class="m-home-nag">
          <div class="m-home-nag-logo">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo-m.png" alt="">
            <span style="position: absolute;right:7rem;top:2rem;" v-if="langFlag" @click="tabLan(false)">EN</span>
            <!--<span style="position: absolute;right:7rem;top:2rem;" v-else  @click="tabLan(true)">中</span>-->
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/hanbuger-m.png" alt="" @click="modelFlag = !modelFlag">
          </div>
        </el-col>
        <el-col class="m-home-nag-model">
          <div class="m-home-nag-logo">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo-m.png" alt="">
            <span style="position: absolute;right:7rem;top:2rem;" v-if="langFlag" @click="tabLan(false)">EN</span>
            <!--<span style="position: absolute;right:7rem;top:2rem;" v-else  @click="tabLan(true)">中</span>-->
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/hanbuger-m.png" alt="" @click="modelFlag = !modelFlag">
          </div>
        </el-col>

        <el-carousel class="home-banner-div" height="120vw">
          <el-carousel-item class="home-banner-div" v-for="(v, k) in bannerList1" :key="k">
            <div class="home-banner-div-item" @click="changePage(k)">
              <img :src="v.src">
            </div>
          </el-carousel-item>
        </el-carousel>
      </div>
    </el-row>
    <div class="m-home-platform" id="tradingPlatform1">
      <div class="m-home-platform-content">
        <div class="m-home-platform-content-title">{{langFlag?langTxt.Zn[7]:langTxt.En[7]}}</div>
        <div class="m-home-platform-content-label">{{langFlag?langTxt.Zn[40]:langTxt.En[28]}}</div>
        <div class="m-home-platform-content-item">
          <a target="_blank" href="https://www.aoex.com/">
            <img src="https://ico-list.oss-cn-hangzhou.aliyuncs.com/cryptovalut/20190402145147nQcAB6Gf5H.png" alt="">
          </a>
          <a target="_blank" href="https://dex.top/trade/ETH_MVC">
            <img src="https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180728141326pNwYwQ8Z5t.png" alt="">
          </a>
          <a target="_blank"  href="https://www.coinegg.com/btc/mvc/">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/coinegglogo.png" alt="">
          </a>
          <a target="_blank" href="https://transfer.swft.pro/swft-v3-en/swft-v3-en-pc/index.html">
            <img src="https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180728142110zBBZeHsWdt.png" alt="">
          </a>
          <a target="_blank"  href="https://www.fubt.top/trade/cny_coin.html?tradeId=15&type=2">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/fubtlogo.png" alt="">
          </a>
          <a target="_blank" href="https://otcbtc.com/">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/otcbtc.png" alt="">
          </a>
          <a target="_blank" href="https://coin2co.in/exchange/C2C_MVC">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/coincoin.png" alt="">
          </a>
          <a target="_blank" href="https://www.oex.com/trade/cny_coin.html?tradeId=39&type=2">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/oexlogo.png" alt="">
          </a>
          <a target="_blank" href="https://yobit.net/en/trade/MVC/BTC">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/yobitlogo.png" alt="">
          </a>
          <a target="_blank" href="https://www.uncoinex.com">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/u-coinlogo.png" alt="">
          </a>
          <a target="_blank" href="https://www.kex.com/trade/cny_coin.html?tradeId=42&type=4">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/kexlogo.png" alt="">
          </a>
          <a target="_blank" href="https://www.rightbtc.com">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/hftlogo.png" alt="">
          </a>
          <a style="background: #2c2c2c" target="_blank" href="https://etherdelta.com/#MVC-ETH">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/etherlogo.png" alt="">
          </a>
          <a style="opacity: 0" target="_blank" href="javascript:void(0)">
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/hftlogo.png" alt="">
          </a>
        </div>
      </div>
    </div>
    <div class="m-home-project" id="m-home-project">
      <div class="m-home-platform-content-title">{{langFlag?langTxt.Zn[8]:langTxt.En[8]}}</div>
      <div class="m-home-project-content">
        <div class="m-home-project-content-item">
          <div>01</div>
          <div>{{langFlag?langTxt.Zn[9]:langTxt.En[9]}}</div>
          <div>{{langFlag?langTxt.Zn[12]:langTxt.En[12]}}</div>
        </div>
      </div>
      <div class="m-home-project-content" >
        <div class="m-home-project-content-item" >
          <div>02</div>
          <div>{{langFlag?langTxt.Zn[10]:langTxt.En[10]}}</div>
          <div>{{langFlag?langTxt.Zn[13]:langTxt.En[13]}}</div>
        </div>
      </div>
      <div class="m-home-project-content" >
        <div class="m-home-project-content-item" >
          <div>03</div>
          <div>{{langFlag?langTxt.Zn[11]:langTxt.En[11]}}</div>
          <div>{{langFlag?langTxt.Zn[14]:langTxt.En[14]}}</div>
        </div>
      </div>
    </div>
    <div class="m-home-technology" id="m-home-technology">
      <div class="m-home-technology-a"></div>
      <div class="m-home-technology-content">
        <div>{{langFlag?langTxt.Zn[15]:langTxt.En[29]}}</div>
        <div style="line-height: 1.5rem;">{{langFlag?langTxt.Zn[41]:langTxt.En[30]}}</div>
      </div>
      <div class="m-home-technology-content-item">
        <div class="m-home-technology-content-item-1" style="margin-left:3rem;">
          <div class="m-home-technology-content-item-1-1">
            <div class="m-home-technology-content-item-1-0">01</div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/lock.png" alt="">
          </div>
          <div class="m-home-technology-content-item-1-2">
            {{langFlag?langTxt.Zn[42]:langTxt.En[31]}}
          </div>
        </div>
        <div class="m-home-technology-content-item-1" style="margin-left:8rem;">
          <div class="m-home-technology-content-item-1-1">
            <div class="m-home-technology-content-item-1-0">02</div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/rocket.png" alt="">
          </div>
          <div class="m-home-technology-content-item-1-2">
            {{langFlag?langTxt.Zn[43]:langTxt.En[32]}}
          </div>
        </div>
        <div class="m-home-technology-content-item-1" style="margin-left:13rem;">
          <div class="m-home-technology-content-item-1-1">
            <div class="m-home-technology-content-item-1-0">03</div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/circle.png" alt="">
          </div>
          <div class="m-home-technology-content-item-1-2">
            {{langFlag?langTxt.Zn[44]:langTxt.En[33]}}
          </div>
        </div>
      </div>
    </div>
    <!--<div class="m-home-team" id="m-home-team">
      <div class="m-home-platform-content-title" style="z-index: 999;position: relative;margin:3rem 0 5rem 0">{{langFlag?langTxt.Zn[45]:langTxt.En[34]}}</div>
      <div class="m-home-platform-content-pmd">
          <div class="m-home-team-item" v-for="(v, k) in photoSrc" :key="k.key">
            <div class="m-home-team-item-img">
              <img :src="v.src">
            </div>
            <div class="m-home-team-item-name">{{langFlag?v.znName:v.enName}}</div>
            <div class="m-home-team-item-position">{{langFlag?v.znPosition:v.enPosition}}</div>
            <div class="m-home-team-item-name-introduction">{{langFlag?v.znIntroduction:v.enIntroduction}}</div>
          </div>
      </div>

    </div>-->
    <div class="m-home-partner" id="m-home-partner">
      <div class="m-home-partner-title">{{langFlag?langTxt.Zn[46]:langTxt.En[42]}}</div>
      <div class="m-home-partner-content">
        <div class="m-home-partner-content-item">
          <div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo1.png" alt="">
          </div>
          <div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo2.png" alt="">
          </div>
        </div>
        <div class="m-home-partner-content-item">
          <div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo3.png" alt="">
          </div>
          <div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo4.png" alt="">
          </div>
        </div>
        <div class="m-home-partner-content-item">
          <div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo6.png" alt="">
          </div>
          <div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo7.png" alt="">
          </div>
        </div>
        <div class="m-home-partner-content-item">
          <div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo8.png" alt="">
          </div>
          <div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo10.png" alt="">
          </div>
        </div>

        <div class="m-home-partner-content-item">
          <div>
            <img src="https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/logo11.png" alt="">
          </div>
          <div>
          </div>
        </div>

      </div>
    </div>
    <div class="m-home-foot">
      <div class="m-home-foot-top">
        <span class="m-home-foot-email"></span>
        <span style="font-size:1.5rem;">mvc@MVChain.net</span>
      </div>
      <div class="m-home-foot-foot">
        <span class="m-home-foot-addr"></span>
        <span style="font-size:1.5rem;">Contract Address：</span>
        <p style="font-size:1.2rem;word-wrap: break-word;">0xb17df9a3b09583a9bdcf757d6367171476d4d8a3</p>
      </div>
      <div class="m-home-foot-mid">
        <a href="https://twitter.com/MaverickChain"></a>
        <a href="https://github.com/mvchain"></a>
      </div>
      <div class="m-home-foot-bottom">
        Maverick Chain is developed and operated by Geniusmobi Co.ltd, a company registrated in Republic of Seychelles.
      </div>
      <div class="m-home-to-top">
        <!--<span @click="backToTop">
          ↑
        </span>-->
      </div>
    </div>
  </div>
</template>

<script>

const bilingual = {
  Zn: [
    '致力于打造区块链行业最好的 BAAS （Blockchain as a Service）服务平台', // 0
    '白皮书下载', // 1
    '新闻', // 2
    '2017/12/2  小牛链与骑行助手达成合作', // 3
    '2017/12/15  MVC上线KEX（韩国交易平台）', // 4
    '2017/11/22   小牛链与Metaverse基金会达成合作', // 5
    '2017/10/11  小牛链即将登陆三个国际交流平台', // 6
    '交易平台', // 7
    '项目介绍', // 8
    '关于小牛链', // 9
    '小牛链愿景', // 10
    '智能合约', // 11
    '小牛链（Maverick Chain）致力于打造区块链行业最好的 BAAS （Blockchain as a Service）服务平台, 我们为区块链开发者提供各公有链的聚合SDK。', // 12
    '当今互联网正进入分布式时代，逐渐从传递信息的互联网演变为交换价值的互联网，Maverick System 将为未来整个人类社会进入透明的、可靠的信用社会打开了大门。', // 13
    'Maverick System 另一大设计特点就是兼容“智能合约”：根据实现任意制定的规则或条件来自动转移数字资产的系统，可以用于将任意状态或条件进行编码并创建合约来确保交易的自动执行。', // 14
    '技术特点', // 15
    '李明肇', // 16
    '林清锐', // 17
    '叶闻达', // 18
    '裴互毫', // 19
    '郭宏才', // 20
    '顾颖', // 21
    '王彬生', // 22
    'CEO', // 23
    'COO', // 24
    'CTO', // 25
    'CMO', // 26
    '导师顾问', // 27
    '顾问', // 28
    '小牛链创始人，曾就职于超大型国企京城控股集团，主要负责集团在欧洲的战略并购工作', // 29
    '小牛链创始人，第二名加入锤子科技的工程师、工号009，锤子手机Smartisam OS的核心开发成员', // 30
    '曾任职于美国道富银行，担任高级工程师，是美国道富银行基金信息管理系统核心开发成员。', // 31
    '比特币早期参与者，区块链项目投资分析师，贵阳区块链组织的前期官方参与者。', // 32
    '币圈黄埔军校创办人、知名区块链行业天使投资人。', // 33
    '资深的区块链行业专家，现任维优创始人兼CEO, 元界基金会主席。', // 34
    '中国社科院研究生院特聘教授，微金融50人论坛执委。', // 35
    '国内最受欢迎的骑乘应用“骑行助手”宣布与Maverick Chain合作。“骑行助手”在中国有超过一百万的用户。开发团队将使用Maverick SDK在应用程序中添加区块链功能，并将发布加密货币Riding Coin。', // 36
    'MVC将于12月15日晚上8点在KEX上进行交换。Maverick Chain是中国最好的BAAS(区块链作为服务)公司，开始进军韩国市场。', // 37
    '我们很高兴地宣布Metaverse基金会已经投资Maverick Chain项目。我们的团队将会在未来的BaaS平台上进行深入的合作。', // 38
    '小牛链近期将准备在三个国际交流平台上进行交易。敬请期待！！！', // 39
    '小牛链MVC已登陆以下平台', // 40
    'Maverick Chain会让你的区块链应用开发更为高效、安全和智能。仅需几个步骤，你就可以轻松的将传统 应用程序转化为区块链应用程序', // 41
    '安全', // 42
    '快速', // 43
    '智能', // 44
    '团队介绍',  // 45
    '合作伙伴',  // 46
    '',  // 47
    '',  // 48
    '',  // 49
    '',  // 50
    '',  // 51
    '',  // 52
    '',  // 53
    '',  // 54
    ''  // 55
  ],
  En: [
    'To be the best Blockchain as a Service (BAAS) platform', // 0
    'Download Whitepaper', // 1
    'NEWS', // 2
    'DEC 2,2017   MVC has partnered with the cycling assistant.', // 3
    'DEC 15，2017  MVC online KEX (Korean trading platform)', // 4
    'NOV 22,2017  MVC has partnered with the Metaverse foundation.', // 5
    'OCT 11,2017  Maverick Chain will be ready to trade on three international exchange ', // 6
    'Exchanges', // 7
    'Introduction', // 8
    'MVC Consortium Blockchain for financial liquidation', // 9
    'TTPay cryptocurrency payment system', // 10
    'TTBTC Fund ', // 11
    'MVC Consortium Blockchain solution can be used on financial assets liquidation between different corporations. MVChain is focused on building a high performance blockchain financial BAAS platform for business. We help our business customers to use blockchain technology to reform traditional finance market. MVChain is a solution for financial assets liquidation between different corporations. Through this consortium blockchain, every members can verify data from the membership corporations while the data keeper corporation can keep their data in secret and encrypted.', // 12
    'TTPay is a cryptocurrency payment platform. Our goal is to become a payment platform in crypto market as Paypal in Fiat market. Our platform provides following products: 1. cryptocurrency payment wallet APP; 2. payment SDK/API for developers; 3. blockchain wallet server for bussiness. We serve both end users and bussiness customers.', // 13
    'TTBTC Bitcoin investment fund is a prudent strategy floating return of crypto assets fund. Our strategy is to make BTC as the investment target for investors to achieve BTC growth in the short and medium term. We adopt real-time dynamic adjustment of the trading model, trading in BTC futures and options market and create stable returns for investors.', // 14
    'Tech Features', // 14
    'Founder of Maverick Chain. He was in charge of M&A business in Jingcheng Holding Europe Gmbh.', // 16
    'Co-founder of Maverick Chain. He was core developer of Smartisam OS. He is an expert in Android development. He contributed several core code in Android system.', // 17
    'He worked as senior engineer in State Street Bank. He was core developer of Information management system of Funds.', // 18
    'Early investor of Bitcoin, Bitcoin analysis. Founder of China Bitcoin Club.', // 19
    'Famous blockchain investor. Bitcoin early investor.', // 20
    'Founder of famous blockchain startup Metaverse. ', // 21
    'Professor of Chinese Academy of Social Sciences. Committee member of We-Finance', // 22
    'Advisor', // 23
    'One of the most popular riding APP “Riding assistant”has announced the cooperation with Maverick Chain. “Riding assistant” has more than one million users in China. The developer team will use Maverick SDK to add block chain function in the APP and will release crypto currency “Riding Coin”', // 24
    'The MVC will exchange on KEX at 8:00 p.m. (GMT) on Dec 15. Maverick Chain is the best BAAS (Blockchain as a Service) company in China Now it is aiming the Korean market!', // 25
    'We are pleased to announce that the Metaverse Foundation has invested in the Maverick Chain project.Our team will cooperate deeply on the BaaS(Blockchain As A Service) platform in the future.', // 26
    'platform within these days. Please pay attention to our further notice.', // 27
    'MVC has landed on the following trading platform', // 28
    'Tech Features', // 29
    'Maverick Chain will make your blockchain application more efficient, secure, and intelligent. With just a few steps, you can easily convert traditional applications into blockchain applications.', // 30
    'Safe', // 31
    'Fast', // 32
    'Smart', // 33
    'Team', // 34
    'Mingzhao Li', // 35
    'Qingrui Lin', // 36
    'Wenda Ye', // 37
    'Huhao Pei', // 38
    'Chandler Guo', // 39
    'Ying Gu', // 40
    'Binsheng Wang', // 41
    'Cooperation Agency', // 42
    '', // 43
    '', // 44
    '', // 45
    '' // 46
  ]
}
export default {
  name: 'HelloWorld',
  beforeDestroy () {
    if (this.interval) {
      clearInterval(this.interval)
    }
  },
  data () {
    return {
      modelFlag: false,
      langFlag: false,
      bannerList: [
        {
          id: 2,
          src: 'https://ico-list.oss-cn-hangzhou.aliyuncs.com/cryptovalut/20190411193418ynw7fCZh82.png'
        },
        {
          id: 1,
          src: 'https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180728172410tz5wKypHSA.jpg'

        }
      ],
      //https://ico-list.oss-cn-hangzhou.aliyuncs.com/cryptovalut/20190402150605JrynSWKdBH.png
      bannerList1: [
        {
          id: 2,
          src: 'https://ico-list.oss-cn-hangzhou.aliyuncs.com/cryptovalut/20190411194034msm4BBPEj5.png'
        },
        {
          id: 1,
          src: 'https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180727202351DzpEefWZMY.jpg'

        }
      ],
      isNagM: false,
      langTxt: bilingual,
      photoLeft: 0,
      isNag: false,
      photoIndex: '',
      announcementHeight: 95,
      announcementHeight1: 8.5,
      interval: null,
      scrolled: false,
      timeLeft: false,
      announcement: true,
      announcement1: true,
      timeRight: false,
      scrolled2: false,
      intervalFlag: true,
      photoSrc: [
        {
          src: 'https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180705134909ewKnnGSSZK.png',
          key: 1,
          znName: bilingual.Zn[16],
          enName: bilingual.En[35],
          znIntroduction: bilingual.Zn[29],
          enIntroduction: bilingual.En[16],
          znPosition: bilingual.Zn[23],
          enPosition: bilingual.Zn[23]
        },
        {
          src: 'https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180705134924CD6zfehKKm.png',
          key: 2,
          znName: bilingual.Zn[17],
          enName: bilingual.En[36],
          znIntroduction: bilingual.Zn[30],
          enIntroduction: bilingual.En[17],
          znPosition: bilingual.Zn[24],
          enPosition: bilingual.Zn[24]
        },
        {
          src: 'https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180705134950jittPzkNPh.png',
          key: 4,
          znName: bilingual.Zn[18],
          enName: bilingual.En[37],
          znIntroduction: bilingual.Zn[31],
          enIntroduction: bilingual.En[18],
          znPosition: bilingual.Zn[25],
          enPosition: bilingual.Zn[25]
        },
        {
          src: 'https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180705134746XFxhyRBdWd.png',
          key: 5,
          znName: bilingual.Zn[21],
          enName: bilingual.En[40],
          znIntroduction: bilingual.Zn[34],
          enIntroduction: bilingual.En[21],
          znPosition: bilingual.Zn[28],
          enPosition: bilingual.En[23]
        },
        {
          src: 'https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180705134851FPrdabiMMQ.png',
          key: 6,
          znName: bilingual.Zn[20],
          enName: bilingual.En[39],
          znIntroduction: bilingual.Zn[33],
          enIntroduction: bilingual.En[20],
          znPosition: bilingual.Zn[27],
          enPosition: bilingual.En[23]
        },
        {
          src: 'https://ttbtc.oss-cn-hangzhou.aliyuncs.com/navigationConsole20180705134935GbwaKTkJ7D.png',
          key: 3,
          znName: bilingual.Zn[22],
          enName: bilingual.En[41],
          znIntroduction: bilingual.Zn[34],
          enIntroduction: bilingual.En[21],
          znPosition: bilingual.Zn[28],
          enPosition: bilingual.En[23]
        }
      ],
      homeFirst: 'home-first1',
      animateFlipInY: '',
      //https://ico-list.oss-cn-hangzhou.aliyuncs.com/cryptovalut/20190402145147nQcAB6Gf5H.png
      platformName: [

        {
          src: 'https://www.coinegg.com/btc/mvc/',
          hover: 'https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/coinegg-hover.png'
        },
        {
          src: 'https://www.oex.com/trade/cny_coin.html?tradeId=39&type=2',
          hover: 'https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/oex-hover.png'
        },
        {
          src: 'https://coin2co.in/exchange/C2C_MVC',
          hover: 'https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/coin2coin-hover.png'
        },
        {
          src: 'https://yobit.net/en/trade/MVC/BTC',
          hover: 'https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/yobit-hover.png'
        },
        {
          src: 'https://www.rightbtc.com',
          hover: 'https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/rightbtc-hover.png'
        },
        {
          src: 'https://etherdelta.com/#MVC-ETH',
          hover: 'https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/ether-hover.png'
        },
        {
          src: 'https://www.uncoinex.com',
          hover: 'https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/ucoin-hover.png'
        },
        {
          src: 'https://www.kex.com/trade/cny_coin.html?tradeId=42&type=4',
          hover: 'https://mvc-site.oss-cn-hangzhou.aliyuncs.com/imgs/kex-hover.png'
        }

      ],
      homeStyle: {},
      positionNum: '',
      targetKey: 0,
      interval5: null,
      navigationList: [
        {
          zn: '首页',
          en: 'Home',
          target: '/',
          mTarget: '/'
        },
        /*{
          zn: '交易平台',
          en: 'Exchanges',
          target: '#tradingPlatform',
          mTarget: '#tradingPlatform1'
        },
        {
          zn: '项目介绍',
          en: 'Introduction',
          target: '#introduction',
          mTarget: '#m-home-project'
        },
        {
          zn: '技术特点',
          en: 'Tech Features',
          target: '#technology',
          mTarget: '#m-home-technology'
        },
        {
          zn: '团队介绍',
          en: 'Team',
          target: '#team',
          mTarget: '#m-home-team'
        },
        {
          zn: '合作伙伴',
          en: 'Cooperative partner',
          target: '#partner',
          mTarget: '#m-home-partner'
        },*/
        {
          zn: 'TTPay',
          en: 'TTPay',
          target: 'https://www.ttpay.info/',
          mTarget: 'https://www.ttpay.info/'
        },
        /*{
          zn: '锁仓平台',
          en: 'MVC Bank',
          target: 'https://mvchain.tech/#/login',
          mTarget: 'https://mvchain.tech/#/login'
        }*/
      ],
      id1: '',
      id2: '',
      id3: '',
      id4: '',
      id5: '',
      id6: ''
    }
  },

  computed: {
    cctv () {
      return '-' + this.photoLeft + 'px'
    }
  },
  components: {
  },
  mounted () {
    let that = this
    window.onresize = function () {
      that.positionNum = 'center center'
    }
    this.interval = setInterval(() => {
      if (that.intervalFlag) {
        if (that.photoLeft > 10000) {
          that.photoLeft = 0
        }
        if (that.timeLeft) {
          that.photoLeft += 8
        } else if (that.timeRight) {
          if (that.photoLeft >= 0) {
            that.photoLeft -= 8
          }
        } else {
          that.photoLeft += 1
        }
      }
    }, 20)
    let language = (navigator.language || navigator.browserLanguage).toLowerCase();
    if (language.indexOf('en') > -1) {
      this.langFlag = false;
    } else {
      this.langFlag = false;
    }
    this.navigationList.forEach((v,k) => {
      if (v.target.indexOf('https') === -1) {
        this[`id${k+1}`] = $(v.target).offset().top;
      }
    })
  },
  created () {
    this.homeStyle = window.innerHeight + 'px'
  },
  methods: {
    announcementHandler () {
      if (this.announcement) {
        if (this.langFlag) {
          this.announcementHeight = 450
        } else {
          this.announcementHeight = 450
        }
        this.announcement = false
      } else {
        this.announcementHeight = 95
        this.announcement = true
      }
    },
    announcementHandler1 () {
      if (this.announcement1) {
        if (this.langFlag) {
          this.announcementHeight1 = 50
        } else {
          this.announcementHeight1 = 70
        }
        this.announcement1 = false
      } else {
        this.announcementHeight1 = 8.5
        this.announcement1 = true
      }
    },

    changePage(t) {
      if (t === 1) {
        window.open('https://erc20.oss-cn-hangzhou.aliyuncs.com/f/MVC_White_Paper.pdf')
      } else {
        window.open('https://www.ttpay.info/')
      }
    },

    divScroll (v) {
      let c = v.srcElement.scrollTop;
      if ((c+2) >= (this.id6-300)) {
        this.targetKey = 5
      } else if  ((c-2) < this.id6 && (c+300) > this.id5) {
        this.targetKey = 4
      } else if ((c-2) < this.id5 && (c+300) > this.id4) {
        this.targetKey = 3
      } else if ((c-2) < this.id4 && (c+300) > this.id3) {
        this.targetKey = 2
      } else if ((c-2) < this.id3 && (c+300) > this.id2) {
        this.targetKey = 1
      } else {
        this.targetKey = 0
      }
      c > 450 ? this.isNag = true : this.isNag = false
      c > 500 ? this.isNagM = true : this.isNagM = false
      this.intervalFlag = c > 3350 && c < 4700
      this.scrolled = c > 1100
      if (c > 1100 && !this.announcement) {
        this.announcementHandler()
      }
      if (c > 1100 && !this.announcement1) {
        this.announcementHandler1()
      }
    },
    getButton (k, t) {
      this.targetKey = k
      this.modelFlag = false
      if (t) {
        this.backToTop(t);
      }
    },
    tabLan (v) {
      v ? this.langFlag = true : this.langFlag = false
    },
    backToTop(name) {
      let that = this;
      name === '#homePage' ? $('#homeCon').animate({scrollTop:that.id1}, 300) :
      name === '#tradingPlatform' ? $('#homeCon').animate({scrollTop:that.id2}, 300) :
      name === '#introduction' ? $('#homeCon').animate({scrollTop:that.id3}, 300) :
      name === '#technology' ? $('#homeCon').animate({scrollTop:that.id4}, 300) :
      name === '#team' ? $('#homeCon').animate({scrollTop:that.id5}, 300) : $('#homeCon').animate({scrollTop:that.id6}, 300);
    }
  },
  beforeDestroy() {
    clearInterval(this.interval5);
  },
}
</script>

<style scoped>
  @import "../assets/css/home.css";
</style>
