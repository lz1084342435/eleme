<template>
  <div id="app">
    <v-header :seller="sellerData"></v-header>

    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评价</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>

    <router-view></router-view>
  </div>
</template>

<script>
import headerPart from "./components/header/header";

const ERR_OK = 0;

export default {
  name: "App",
  data() {
    return {
      sellerData: {}
    };
  },
  components: {
    "v-header": headerPart
  },
  created() {
    this.$http.get("api/seller").then(res => {
      if (res.body.errno === ERR_OK) {
        this.sellerData = res.body.data;
        console.log(this.sellerData);
      }
    });
  }
};
</script>

<style>
#app .tab {
  position: relative;
  display: flex;
  width: 100%;
  height: 40px;
  font-size: 14px;
  color: rgb(77, 85, 93);
}
.tab::after {
  position: absolute;
  content: " ";
  width: 100%;
  left: 0;
  bottom: 0;
  border-bottom: 1px solid rgba(7, 17, 27, 0.1);
}
@media (-webkit-min-device-pixel-ratio: 1.5), (min-device-pixel-ratio: 1.5) {
  -webkit-transform: scaleY(0.7);
  transform: scaleY(0.7);
}
@media (-webkit-min-device-pixel-ratio: 2), (min-device-pixel-ratio: 2) {
  -webkit-transform: scaleY(0.7);
  transform: scaleY(0.5);
}
.tab .tab-item {
  flex: 1;
  line-height: 40px;
  text-align: center;
}
.tab-item > a {
  display: block;
}

.router-link-active {
  color: rgb(240, 20, 20);
}
</style>
