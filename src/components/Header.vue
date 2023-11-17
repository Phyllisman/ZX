<template>
  <div style="display: flex; line-height: 60px">
    <div style="margin-top: 8px">
      <i :class="icon" style="font-size: 20px; cursor:pointer;" @click="collapse"></i>
    </div>
    <div style="flex: 1; text-align: center; font-size: 34px;">
      <span>欢迎来到用户管理系统</span>
    </div>
    <span>王小虎</span>
    <el-dropdown>
      <i class="el-icon-user" style="margin-left: 5px">
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item @click.native="toUser">个人中心</el-dropdown-item>
          <el-dropdown-item @click.native="logout">退出登录</el-dropdown-item>
        </el-dropdown-menu>
      </i>
    </el-dropdown>
  </div>
</template>

<script>
export default {
  name: 'Header',
  props:{
    icon:String
  },
  methods: {
    toUser(){
      console.log('to_user')
    },
    logout(){
      console.log('logout')
    },
    collapse(){
      //传给父组件
      this.$emit('doCollapse')
    }
  }
}
</script>

<style>
</style>