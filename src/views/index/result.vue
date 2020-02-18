<template>
  <section>
    <!--工具条-->
    <el-col :span="24" class="toolbar" style="padding-bottom: 0px;">
      <el-form :inline="true" :model="filters">
        <el-form-item>
          <el-input v-model="filters.name" placeholder="姓名"></el-input>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" v-on:click="getFilterSearch">查询</el-button>
        </el-form-item>
      </el-form>
    </el-col>

    <!--列表-->
    <el-table :border="true" :data="resultArr" highlight-current-row v-loading="loading" style="width: 100%;">
      <!-- <el-table-column type="index" width="60"></el-table-column> -->
      <el-table-column prop="name" label="所属小区"></el-table-column>
      <!-- <el-table-column prop="sex" label="总人数" :formatter="formatSex" sortable></el-table-column> -->
      <el-table-column prop="sex" label="总人数"></el-table-column>
      <el-table-column prop="age" label="老三类小计（人）"></el-table-column>
      <el-table-column prop="birth" label="湖北籍人员（人）"></el-table-column>
      <el-table-column prop="addr" label="近期有疫情居住或旅行史(人)"></el-table-column>
      <el-table-column prop="addr" label="近期与疫区外来人员密切接触式(人)"></el-table-column>
      <el-table-column prop="addr" label="与疑似和确诊病人有接触(人)"></el-table-column>
      <el-table-column prop="addr" label="新三类小计(人)"></el-table-column>
      <el-table-column prop="addr" label="与到过武汉的人有接触史(人)"></el-table-column>
    </el-table>
    <!-- 分页 -->
    <!-- <div class="pagination">
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page.sync="currentPage"
        :page-size="100"
        layout="total, prev, pager, next"
        :total="1000"
      ></el-pagination>
    </div> -->
  </section>
</template>
<script>
import { getUserList } from "../../api/api";
//import NProgress from 'nprogress'
export default {
  data() {
    return {
      filters: {
        name: ""
      },
      loading: false,
      resultArr: [],

      currentPage: 1
    };
  },
  methods: {
    // handleSizeChange(val) {
    //   console.log(`每页 ${val} 条`);
    // },
    // // 切换分页
    // handleCurrentChange(val) {
    //   console.log(`当前页: ${val}`);
    // },

    // 进行查询
    getFilterSearch() {}
  },
  mounted() {}
};
</script>

<style scoped lang="scss">
.pagination{
    display: flex;
    justify-content: flex-end;
    margin-top: 20px;
}
</style>