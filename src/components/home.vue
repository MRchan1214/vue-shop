<template>
  <div class="home">
    <div>
      <el-button type="info" @click="loginout">退出</el-button>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {

    }
  },
  methods: {
    loginout () {
      window.localStorage.clear()
      this.$router.push({
        path: '/login'
      })
    }
  }
}
</script>

<style>
</style>
