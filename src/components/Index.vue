<template>
  <div v-set-view  :class="indexStyle.warp">
  <div :class="[indexStyle.cointer]">
    <div :class="indexStyle.cointerbg">
        <div v-direct="this">
        <div v-cet :class="indexStyle.usergroup">
        <div :class="indexStyle.userface"></div>
        <div :class="[indexStyle.username, globalStyle.center]">{{ userInfo.name }}</div>
        </div>
        </div>
    </div>

     <div :class="[indexStyle.warp, globalStyle.icfont]"></div>
  </div>

  <div :class="indexStyle.content">
    </div>
  </div>
</template>

<script>
import globalStyle from '../assets/scss/global.scss'
import indexStyle from '../assets/scss/index.scss'

import { CheckLogin, repeatMobile } from '../services/Global'
export default {
  name: 'hello',
  components: {
  },
  data () {
    return {
      globalStyle,
      indexStyle,
      isLogin: CheckLogin(this),
      title: '个人中心',
      userInfo: this.userInfo()
    }
  },
  methods: {
    userInfo () {
      // console.log(this)
      if (this.$cookie.get('token')) {
        let mobile = this.$cookie.get('mobile')
        return {name: repeatMobile({mobile: mobile})}
      } else {
        return {name: '用户登录'}
      }
    }
  },
  created () {

  }
}
</script>
