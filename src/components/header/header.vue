<template>
  <div class="headerPart">
    <div class="sellerInfo">
      <div class="avatar">
        <img width="64" height="64" :src="seller.avatar" alt="avatar">
      </div>

      <div class="infoContnt">
        <div class="brand">
          <span class="brand-img"></span>
          <span class="name">{{seller.name}}</span>
        </div>
        <div class="description">{{seller.description}}/{{seller.deliveryTime}}分钟送达</div>
        <div v-if="seller.supports" class="supports">
          <span :class="iconMap[seller.supports[0].type]" class="support-icon"></span>
          <span class="support-content">{{seller.supports[0].description}}</span>
        </div>
      </div>

      <div class="support-count" v-if="seller.supports">
        <span>{{seller.supports.length}}个</span>
        <span class="icon-keyboard_arrow_right"></span>
      </div>
    </div>

    <div class="bulletin">
      <span class="bulletin-title"></span><span class="bulletin-content">{{seller.bulletin}}</span>
      <span class="icon-keyboard_arrow_right"></span>
    </div>

    <div class="background">
      <img :src="seller.avatar" alt="background">
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
export default {
  name: "headerPart",
  data() {
    return {};
  },
  props: {
    seller: {
      type: Object
    }
  },
  created() {
    this.iconMap = ["decrease", "discount", "guarantee", "invoice", "special"];
    this.iconMap = ["decrease", "discount", "guarantee", "invoice", "special"];
  }
};
</script>

<style scoped>
@import "./../../common/css/sell-icon.css";
.headerPart {
  position: relative;
  background-color: rgba(7, 17, 27, 0.4);
}
.sellerInfo {
  position: relative;
  padding: 24px 12px 18px 24px;
  font-size: 0px;
}
.avatar {
  vertical-align: top;
  display: inline-block;
}
.avatar img {
  border-radius: 2px;
}
.infoContnt {
  margin-left: 16px;
  display: inline-block;
  color: #ffffff;
}
.brand {
  vertical-align: top;
  margin: 2px 0 8px 0;
}
.brand-img {
  vertical-align: middle;
  display: inline-block;
  margin-right: 6px;
  width: 30px;
  height: 18px;
  line-height: 18px;
  background: url("./img/brand@2x.png") no-repeat;
  background-size: 30px 18px;
}
.brand .name {
  vertical-align: middle;
  font-size: 16px;
}
.description {
  margin-bottom: 10px;
  font-size: 12px;
}
.supports {
  font-size: 10px;
  display: flex;
  align-items: center;
}
.support-icon {
  vertical-align: top;
  margin-right: 4px;
  display: inline-block;
  width: 12px;
  height: 12px;
  background-size: 12px 12px;
  background-repeat: no-repeat;
}
.support-content {
  display: inline-block;
  font-size: 10px;
  height: 12px;
  line-height: 14px;
}
.decrease {
  background: url("./img/decrease_1@2x.png");
  background-size: 12px 12px;
}
.discount {
  background: url("./img/discount_1@2x.png");
  background-size: 12px 12px;
}
.guarantee {
  background: url("./img/guarantee_1@2x.png");
  background-size: 12px 12px;
}
.invoice {
  background: url("./img/invoice_1@2x.png");
  background-size: 12px 12px;
}
.special {
  background: url("./img/special_1@2x.png");
  background-size: 12px 12px;
}
.support-count {
  position: absolute;
  right: 12px;
  bottom: 18px;
  z-index: 68;
  padding: 0px 8px;
  height: 24px;
  line-height: 28px;
  background-color: rgba(0, 0, 0, 0.2);
  border-radius: 14px;
  color: #ffffff;
  font-size: 14px;
}
.icon-keyboard_arrow_right {
  vertical-align: middle;
  font-size: 14px;
}
.bulletin {
  position: relative;
  height: 28px;
  padding: 0px 27px 0 12px;
  background-color: rgba(7, 17, 27, 0.2);
  line-height: 32px;
  color: #ffffff;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.bulletin-title {
  display: inline-block;
  width: 22px;
  height: 12px;
  margin-right: 4px;
  background: url("./img/bulletin@2x.png");
  background-size: 22px 12px;
  background-repeat: no-repeat;
}
.bulletin-content {
  vertical-align: top;
  font-size: 10px;
}
.bulletin .icon-keyboard_arrow_right {
  position: absolute;
  display: inline-block;
  height: 10px;
  line-height: 10px;
  right: 12px;
  top: 50%;
  margin-top: -5px;
  vertical-align: middle;
  font-size: 14px;
}
.background {
  position: absolute;
  left: 0px;
  top: 0px;
  width: 100%;
  height: 100%;
  background: rgba(7, 17, 27, 0.2);
  filter:blur(10px);
  z-index: -1;
}
.background>img {
  width: 100%;
  height: 100%;
}
</style>
