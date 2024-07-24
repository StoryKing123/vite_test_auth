<script setup>
import { ref } from 'vue'
import { onMounted } from 'vue'

const corpid = 'wwcfe75b0c5adcd008'
const callbackUrl = window.location.href
onMounted(() => {
  console.log(callbackurl)
  try {
    wx.qy.login({
      success: function (res) {
        if (res.code) {
          console.log(res)
          console.log('222')
        } else {
          console.log('登录失败！' + res.errMsg)
        }
      }
    });
  } catch (error) {
    console.error(error)
  }


})
const login = () => {
  console.log('login')
  window.location.href = `https://open.weixin.qq.com/connect/oauth2/authorize?appid=${corpid}&redirect_uri=${callbackUrl}&response_type=code&scope=snsapi_base#wechat_redirect`


}



defineProps({
  msg: String,
})

const count = ref(0)
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">create-vue</a>, the official Vue + Vite
    starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
  <button @click="login">login</button>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
