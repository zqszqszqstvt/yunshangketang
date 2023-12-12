<template>
  <div class="header">
    <div class="left">
      <img class="logo" :src="logoImg" alt="" />
      <div class="title">
        <img :src="titleImg" alt="" />
      </div>
    </div>
    <div class="navigation">
      <div
        v-for="nav in navList"
        :key="nav.code"
        :class="['nav', { active: activeNav === nav.code }]"
        @click="changeNav(nav.code)"
      >
        {{ nav.label }}
      </div>
    </div>
  </div>
</template>

<script>
import logoImg from "@/assets/layout/logo.png";
import titleImg from "@/assets/layout/title.png";
export default {
  name: "HeaderBar",
  components: {},
  mounted() {},
  data() {
    return {
      logoImg,
      titleImg,
      activeNav: "home",
      navList: [
        {
          label: "首页",
          code: "home",
        },
        {
          label: "课程学习",
          code: "study",
        },
        {
          label: "信息发布",
          code: "publish",
        },
        {
          label: "能力自画像",
          code: "self",
        },
        {
          label: "登录/注册",
          code: "login",
        },
      ],
    };
  },
  methods: {
    changeNav(code) {
      this.activeNav = code;
      // todo 页面跳转
    },
  },
};
</script>
<style scoped>
.header {
  height: 68px;
  background-color: #581bb7;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 40px 0 30px;
  .left {
    display: flex;
    align-items: center;
    .logo {
      height: 40px;
    }
    .title {
      position: relative;
      margin-left: 30px;
      padding-left: 30px;
      display: flex;
      align-items: center;
      img {
        height: 24px;
      }
    }
    .title::before {
      content: "";
      width: 1px;
      height: 30px;
      background: #ffffff;
      opacity: 0.25;
      position: absolute;
      left: 0;
      top: -2px;
    }
  }
  .navigation {
    display: flex;
    height: 100%;
    .nav {
      display: flex;
      height: 100%;
      align-items: center;
      position: relative;
      cursor: pointer;
      font-size: 16px;
      font-family: PingFangSC, PingFang SC;
      font-weight: 400;
      color: #ffffff;
      line-height: 22px;
      margin-left: 60px;
      transition: all ease-in-out 0.3s;
      &::after {
        content: none;
        position: absolute;
        background: url("@/assets/layout/triangle.png") no-repeat;
        left: calc(50% - 8px);
        bottom: 0;
        width: 16px;
        height: 10px;
      }
      &:hover {
        font-weight: 600;
      }
      &.active {
        font-weight: 600;
        &::after {
          content: "";
        }
      }
    }
  }
}
</style>
