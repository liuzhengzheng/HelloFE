<template>
  <div class="layout">
    <i-layout>
      <i-sider breakpoint="md" collapsible :collapsed-width="78" v-model="isCollapsed" width="160">
        <div class="layout-logo">
          <img src="../../assets/logo.png" alt="logo"/>
        </div>
        <i-menu :active-name="activeName" theme="dark" width="auto" :class="menuitemClasses">
          <i-menuitem v-for="(item, index) in nav" :key="index" :name="item.code">
            <a :href="'#'+item.code">{{item.name}}</a>
          </i-menuitem>
        </i-menu>
        <div slot="trigger"></div>
      </i-sider>
      <i-layout>
        <i-content :style="{padding:'0 30px', height: '100vh', overflow:'auto'}">
          <router-view></router-view>
        </i-content>
      </i-layout>
    </i-layout>
  </div>
</template>
<script>
import {Layout, Sider, Menu, MenuItem, Content} from 'iview'
import { Resources } from '@/assets/data/sdata.js'
export default {
  data () {
    return {
      nav: Resources,
      isCollapsed: false,
      activeName: this.$route.hash ? this.$route.hash.split('#')[1] : '1-1'
    }
  },
  computed: {
    menuitemClasses: function () {
      return [
        'menu-item',
        this.isCollapsed ? 'collapsed-menu' : ''
      ]
    }
  },
  created () {
    // console.log(this.$route.hash)
  },
  components: {
    'i-layout': Layout,
    'i-sider': Sider,
    'i-menu': Menu,
    'i-menuitem': MenuItem,
    'i-content': Content
  }
}
</script>
<style scoped>
.layout{
  border: 1px solid #d7dde4;
  background: #ffffff;
  position: relative;
  border-radius: 4px;
  overflow: hidden;
}
.menu-item a{
  color: inherit;
  overflow: hidden;
  width: 100px;
  text-overflow: ellipsis;
  white-space: nowrap;
  vertical-align: bottom;
  transition: width .2s ease .2s;
}
.menu-item i{
  transform: translateX(0px);
  transition: font-size .2s ease, transform .2s ease;
  vertical-align: middle;
  font-size: 16px;
}
.collapsed-menu span{
  width: 0px;
  transition: width .2s ease;
}
.collapsed-menu i{
  transform: translateX(5px);
  transition: font-size .2s ease .2s, transform .2s ease .2s;
  vertical-align: middle;
  font-size: 22px;
}
.ivu-menu-dark.ivu-menu-vertical .ivu-menu-item-active:not(.ivu-menu-submenu), .ivu-menu-dark.ivu-menu-vertical .ivu-menu-submenu-title-active:not(.ivu-menu-submenu) {
  color: #fff;
  border-right: 2px solid #2d8cf0;
  background: #2d8cf0;
}
.ivu-menu-vertical .ivu-menu-item, .ivu-menu-vertical .ivu-menu-submenu-title {
  border-bottom: 1px solid #999;
}
</style>
<style>
.layout .ivu-layout-sider-zero-width-trigger{
  top: 2px;
  right: -30px;
  width: 30px;
  height: 30px;
  line-height: 30px;
}
</style>
