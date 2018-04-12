<template>
  <div id="topbar">
      <div class="logo">
          VueResume
      </div>
      <div class="actions">
         <el-button round>登录</el-button>
  <el-button type="primary" round>注册</el-button>
      </div>
  </div>
</template>
<style lang="scss">
#topbar{
   display: flex;
   justify-content: space-between;
   padding:16px;
   font-size: 20px;
   align-items: center;
}
</style>
