<template>
  <a-layout-header
    style="
			padding: 0px;
			height: 48px;
			line-height: 48px;
			width: 100%;
			z-index: 19;
		"
  >
    <div class="global-header">
      <div class="menu-trigger" style="margin-right:20px">
        <a-icon
          class="trigger"
          :type="$store.state.collapsed ? 'menu-unfold' : 'menu-fold'"
          @click="check"
        />
      </div>
      <div class="left">权限管理 / {{ $route.meta.title }}</div>
      <div class="right">
        <Notice />
        <div class="user">
          下午好！
          <span>{{ $store.state.user }}</span>
        </div>
        <div class="out" @click="out">退出</div>
      </div>
    </div>
  </a-layout-header>
</template>
<script>
import Notice from '@/components/notice'
export default {
  components: { Notice },
  methods: {
    check() {
      this.$store.commit('collapsed', !this.$store.state.collapsed)
    },
    out() {
      localStorage.clear('auth-info')
      this.$router.push('/login')
    },
  },
}
</script>
<style lang="less" scoped>
.global-header {
  position: relative;
  display: flex;
  align-items: center;
  height: 100%;
  padding: 0 16px;
  background: #fff;
  box-shadow: 0 1px 4px rgba(0, 21, 41, 0.08);
  .left {
    flex: 1 1 0%;
  }
  .right {
    display: flex;
    float: right;
    height: 48px;
    margin-left: auto;
    overflow: hidden;
  }
}
.user {
  line-height: 48px;
  & > span {
    color: #58a3f7;
    cursor: pointer;
  }
}
.out {
  margin-left: 10px;
  cursor: pointer;
}
</style>
