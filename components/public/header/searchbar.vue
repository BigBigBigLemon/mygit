<template>
  <div class='search-panel'>
      <el-row class="m-header-searchbar">
          <el-col :span="3" class="left">
              <img src="//s0.meituan.net/bs/fe-web-meituan/e5eeaef/img/logo.png" alt="丑团">
          </el-col>
          <el-col :span="15" class="center">
              <div class="center">
                  <div class="wrapper">
                     <el-input
                        placeholder="搜索商家或地点"
                        v-model="search"
                        @focus="handleFocusSearch"
                        @blur="handleBlurSearch"
                     ></el-input>
                    <button class="el-button el-button--primary">
                        <i class="el-icon-search"></i>
                    </button>
                    <dl class="hotPlace" v-if="isHotPlace">
                        <dt>热门搜索</dt>
                        <dd>火锅</dd>
                        <dd>火锅</dd>
                        <dd>火锅</dd>
                        <dd>火锅</dd>
                    </dl>
                    <dl class="searchList" v-if="isSearchList">
                        <dd>小龙虾</dd>
                        <dd>小龙虾</dd>
                        <dd>小龙虾</dd>
                        <dd>小龙虾</dd>
                        <dd>小龙虾</dd>
                    </dl>
                  </div>
                  <p class="suggest">
                      <a href="#">故宫博物院</a>
                      <a href="#">故宫博物院</a>
                      <a href="#">故宫博物院</a>
                      <a href="#">故宫博物院</a>
                      <a href="#">故宫博物院</a>
                      <a href="#">故宫博物院</a>
                  </p>
                  <ul class="nav">
                      <li><nuxt-link to="/takeout">美团外卖</nuxt-link></li>
                      <li><nuxt-link to="/takeout">猫眼电影</nuxt-link></li>
                      <li><nuxt-link to="/takeout">美团酒店</nuxt-link></li>
                      <li><nuxt-link to="/takeout">民宿公寓</nuxt-link></li>
                      <li><nuxt-link to="/takeout">商家入驻</nuxt-link></li>
                      <li><nuxt-link to="/takeout">美团公益</nuxt-link></li>
                  </ul>
              </div>
          </el-col>
          <!-- <el-col :span="6" class="right">3</el-col> -->
      </el-row>
  </div>
</template>

<script>

export default {
  data () {
    return {
      search: '',
      isFocus: false
    }
  },
  components: {},

  computed: {
    isHotPlace () {
      return this.isFocus && !this.search
    },
    isSearchList () {
      return this.isFocus && this.search
    }
  },
  mounted () {},

  methods: {
    handleFocusSearch () {
      this.isFocus = true
    },
    handleBlurSearch () {
      let _this = this
      setTimeout(function () {
        _this.isFocus = false
      }, 200)
    }
  }

}

</script>
<style scoped>

</style>
