<template>
  <div class="card" style="margin-bottom: 10px">
    <el-input
        style="width: 240px; margin-right: 8px"
        v-model="data.input"
        placeholder="请输入查询内容"
        prefix-icon="Search"
    ></el-input>
    <el-button type="primary" @click="load">查询</el-button>
    <el-button type="primary" style="background-color: #e86e6e;" @click="reset">重置</el-button>
  </div>
  <div class="card">
    <el-button type="primary">新增</el-button>
    <el-button type="primary" style="background-color: #e86e6e;">批量删除</el-button>
  </div>
  <div class="card">
    <el-table :data="data.tableData"stripe >
      <el-table-column label="用户ID" prop="userId"/>
      <el-table-column label="名称" prop="username"/>
      <el-table-column label="密码" prop="password"/>
      <el-table-column label="邮箱" prop="email"/>
      <el-table-column label="手机号" prop="phone"/>
    </el-table>
    <div style="margin-top:10px">
      <el-pagination v-model:current-page="data.pageNum"
                     v-model:page-size="data.pageSize"
                     :page-size="[5,10,15,20]"
                     background
                     layout="total,size,prev,pager,next,jumper"
                     :total="data.total"
    />
    </div>
  </div>


</template>

<script setup>
import {reactive} from "vue";
import  {Search} from "@element-plus/icons-vue";
const data=reactive({
  input:null,
  pageNum:1,
  pageSize:10,
  total:50,
  tableData:[
    {userId:1,username:'zhangsan',password:'1234567890',email:'123@163.com',phone:'1234567890'}


  ]
})


</script>
<style scoped>
.card{
  background-color: white;
  padding: 10px;
  border-radius: 5px;
  box-shadow:0 0 8px rgb(192, 192, 192);
}
</style>



