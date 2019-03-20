<template>
  <div>
     <x-header :right-options="{showMore: false}" :left-options="{showBack: true}">我爱阅读</x-header>
    <group title="用户">
      <x-input title="手机号" mask="999 9999 9999" v-model="phone" :max="13" is-type="china-mobile"></x-input>
      <x-input title="密码" type='password' v-model="password" :max="9"></x-input>
    </group>
   <x-button type="primary" @click.native='login' action-type="button">登录</x-button>
  </div>
</template>

<script>
import { AlertModule, Group, Cell, XHeader, XInput, XButton, Alert } from 'vux'

export default {
  components: {
    XButton,
    XInput,
    XHeader,
    Group,
    Cell,
    AlertModule,
    Alert
  },
  methods: {
    login () {
      if (this.password === '123456') {
        this.$router.push({ path: '/' })
      } else {
        AlertModule.show({
          title: '登录失败',
          content: '密码错误'
        })
      }
    }
  },
    created () {
    let _this = this
    this.$http.get('http://localhost:3000/api/news').then(({data}) => {
      console.log(data)
      var new_data = data.map((item, index) => ({
        title: item.title,
        src: item.src,
        desc: item.content
      }))
      console.log(new_data)
      _this.list = new_data
    })
  },
  data () {
    return {
      phone: ' ',
      password: ' '
    }
  }
}
</script>
