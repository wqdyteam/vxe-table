<template>
  <div class="page-layout-container">
    <div class="page-layout-aside">
      <div>
        <button @click="changeTheme">切换主题</button>
      </div>
      <div>
        <button @click="changeLang('zh-CN')">中文</button>
        <button @click="changeLang('en-US')">英文</button>
      </div>
      <RouterLink  class="link" v-for="(item, index) in navList" :key="index" :to="item.routerLink">{{ item.name }}</RouterLink>
    </div>
    <div class="page-layout-body">
      <RouterView />
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import { VxeUI } from '../packages'

const navList = ref([
  { name: 'Home', icon: 'vxe-icon-user-fill', routerLink: { path: '/' } },
  { name: 'ToolbarTest', routerLink: { name: 'ToolbarTest' } },
  { name: 'TableTest1', routerLink: { name: 'TableTest1' } },
  { name: 'TableTest2', routerLink: { name: 'TableTest2' } },
  { name: 'TableTest3', routerLink: { name: 'TableTest3' } },
  { name: 'TableTest4', routerLink: { name: 'TableTest4' } },
  { name: 'TableTest5', routerLink: { name: 'TableTest5' } },
  { name: 'TableTest6', routerLink: { name: 'TableTest6' } },
  { name: 'TableTest7', routerLink: { name: 'TableTest7' } },
  { name: 'TableTest8', routerLink: { name: 'TableTest8' } },
  { name: 'TableTest9', routerLink: { name: 'TableTest9' } },
  { name: 'TableTest10', routerLink: { name: 'TableTest10' } },
  { name: 'GridTest1', routerLink: { name: 'GridTest1' } },
  { name: 'GridTest2', routerLink: { name: 'GridTest2' } },
  { name: 'GridTest3', routerLink: { name: 'GridTest3' } },
  { name: 'TestKeepTest1', routerLink: { name: 'TestKeepTest1' } },
  { name: 'TestKeepTest2', routerLink: { name: 'TestKeepTest2' } },
  { name: 'TestKeepTest3', routerLink: { name: 'TestKeepTest3' } }
])

const theme = ref((localStorage.getItem('VXE_THEME') as 'default' | 'dark') || 'default')
VxeUI.setTheme(theme.value)
const changeTheme = () => {
  const themeName = VxeUI.getTheme() === 'dark' ? 'default' : 'dark'
  theme.value = themeName
  VxeUI.setTheme(themeName)
  localStorage.setItem('VXE_THEME', themeName)
}

VxeUI.setLanguage((localStorage.getItem('VXE_LANGUAGE') as 'zh-CN' | 'en-US') || 'zh-CN')
const changeLang = (lang: 'zh-CN' | 'en-US') => {
  VxeUI.setLanguage(lang)
  localStorage.setItem('VXE_LANGUAGE', lang)
}
</script>

<style lang="scss" scoped>
.page-layout-container {
  display: flex;
  flex-direction: row;
}
.page-layout-aside {
  flex-shrink: 0;
  width: 200px;
  padding: 16px;
  border-right: 1px solid #d0d7de;
  .link {
    display: block;
  }
}
.page-layout-body {
  flex-grow: 1;
  padding: 16px;
  overflow: auto;
}
</style>
