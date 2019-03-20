<template>
  <div>
    <x-header :right-options="{showMore: true}" :left-options="{showBack: false}">我爱阅读1</x-header>
    <swiper :list="demo01_list" v-model="demo02_index" ></swiper>
    <grid :cols="4" :show-lr-borders="false">
      <grid-item :label="('Grid')" v-for="i in 4" :key="i">
        <img slot="icon" src="../assets/app.png">
      </grid-item>
    </grid>
    <panel :header="'推荐'" :footer="footer" :list="list" :type="type"></panel>
    <tabbar>
      <tabbar-item>
        <img slot="icon" src="../assets/sta2.png">
        <span slot="label">收藏</span>
      </tabbar-item>
      <tabbar-item show-dot>
        <img slot="icon" src="../assets/menu-fold.png">
        <span slot="label">菜单</span>
      </tabbar-item>
      <tabbar-item selected >
        <img slot="icon" src="../assets/ic-settings.png">
        <span slot="label">设置</span>
      </tabbar-item>
      <tabbar-item badge="2">
        <img slot="icon" src="../assets/user.png">
        <span slot="label">我的</span>
      </tabbar-item>
    </tabbar>
  </div>
</template>

<script>
import { Tabbar, TabbarItem, Group, Cell, XHeader, Swiper, Grid, GridItem, Panel } from 'vux'

export default {
  components: {
    Panel,
    Grid,
    GridItem,
    Swiper,
    XHeader,
    Tabbar,
    TabbarItem,
    Group,
    Cell
  },
  data () {
    return {
      demo01_list: baseList,
      demo02_index: 1,
      type: '1',
      list: [{
        src: 'http://somedomain.somdomain/x.jpg',
        fallbackSrc: 'http://placeholder.qiniudn.com/60x60/3cc51f/ffffff',
        title: '标题一',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: '/component/cell'
      }, {
        src: 'http://placeholder.qiniudn.com/60x60/3cc51f/ffffff',
        title: '标题二',
        desc: '由各种物质组成的巨型球状天体，叫做星球。星球有一定的形状，有自己的运行轨道。',
        url: {
          path: '/component/radio',
          replace: false
        },
        meta: {
          source: '来源信息',
          date: '时间',
          other: '其他信息'
        }
      }]
    }
  }
}

const baseList = [{
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vvsr72j20p00gogo2.jpg',
  title: '送你一朵fua'
}, {
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg',
  title: '送你一辆车'
}, {
  url: 'javascript:',
  img: 'https://static.vux.li/demo/5.jpg', // 404
  title: '送你一次旅行',
  fallbackImg: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw50iwj20ff0aaaci.jpg'
}]
</script>