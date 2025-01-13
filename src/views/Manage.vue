<template>
  <div id="app">
    <!--项目头部部分开始-->
    <div style="height: 80px; background-color: #3c7fff; display: flex; align-items: center;">
      <!-- 左侧 Logo -->
      <div style="margin-left: 20px;">
        <img src="https://img.alicdn.com/imgextra/i4/O1CN01GqQHlL1WjUZvJdIuA_!!6000000006860-0-tps-1920-1080.jpg" alt="Logo" style="width: 50px; height: 50px; object-fit: cover;">
        <span style="color: white; font-size: 18px; margin-left: 10px;">仰恩湖水资源管理系统</span>
      </div>
      <div style="flex-grow: 1;"></div>
      <!-- 右侧 用户名 -->
      <div style="margin-right: 20px; color: white; font-size: 16px;">
        用户名
      </div>
    </div>
    <!--项目头部部分结束-->
    <!--页面布局左侧开始-->
    <div style="display: flex">
      <div style="width: 200px;border-right:1px solid #ddd;min-height: calc(100vh - 80px)">
        <el-menu router :default-active="router.currentRoute.value.path" style="border: 0">
          <el-menu-item index="/"><el-icon><House/></el-icon>系统首页</el-menu-item>
          <el-menu-item>河段管理</el-menu-item>
          <el-menu-item>水位监测</el-menu-item>
          <el-menu-item>数据展示</el-menu-item>
          <el-sub-menu index="1">
            <template #title>
              <el-icon></el-icon>
              <span>水质监测</span>
            </template>
            <el-menu-item index="/manage/data">浑浊度监测</el-menu-item>
            <el-menu-item>PH值监测</el-menu-item>
            <el-menu-item>溶解度值监测</el-menu-item>
          </el-sub-menu>
          <el-menu-item>用户举报</el-menu-item>
          <el-menu-item index="/manage/User"><el-icon><User/></el-icon>用户信息</el-menu-item>
        </el-menu>
      </div>
      <!--页面布局左侧结束-->
      <!--页面布局右侧开始-->
      <div style="flex: 1;width: 0;background-color: #e9eaff ;padding: 10px">
        <RouterView/>
      </div>
      <!--页面布局右侧结束-->
    </div>
  </div>
</template>

<script setup>
import request from "@/utils/request.js";
import { reactive } from "vue";
import router from "@/router/index.js";
import { House, User } from "@element-plus/icons-vue";

const data = reactive({
  usersList: []
});

request.get('/users/{userId}').then(res => {
  console.log(res);
  data.usersList = res.data;
});

const logout = () => {
  localStorage.removeItem('token');
  router.push('/login');
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.el-dropdown-link {
  cursor: pointer;
  color: white;
}
</style>