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
    <el-table :border="true" :data="detailArr" v-loading="loading" style="width: 100%;">
      <el-table-column label="个人信息">
        <el-table-column prop="name" label="填写时间"></el-table-column>
        <el-table-column prop="sex" label="姓名"></el-table-column>
        <el-table-column prop="age" label="性别"></el-table-column>
        <el-table-column prop="birth" label="年龄"></el-table-column>
        <el-table-column prop="addr" label="身份证号"></el-table-column>
        <el-table-column prop="addr" label="联系方式"></el-table-column>
        <el-table-column prop="addr" label="现住地小区"></el-table-column>
        <el-table-column prop="addr" label="现住地房号"></el-table-column>
        <el-table-column prop="addr" label="居住类型"></el-table-column>
        <el-table-column prop="addr" label="家中常驻人数"></el-table-column>
      </el-table-column>
      <el-table-column label="出行情况">
        <el-table-column prop="addr" label="是否来自疫情发放地区"></el-table-column>
        <el-table-column prop="addr" label="接触过外市的来访人员"></el-table-column>
        <el-table-column prop="addr" label="是否去过外市"></el-table-column>
        <el-table-column prop="addr" label="所到城市"></el-table-column>
        <el-table-column prop="addr" label="所到时间"></el-table-column>
        <el-table-column prop="addr" label="出行方式"></el-table-column>
      </el-table-column>
      <el-table-column label="健康状况">
        <el-table-column prop="addr" label="身体健康状况"></el-table-column>
        <el-table-column prop="addr" label="今日测量体温(℃)"></el-table-column>
        <el-table-column prop="addr" label="是否有以下症状"></el-table-column>
      </el-table-column>
      <el-table-column label="诊疗情况">
        <el-table-column prop="addr" label="诊疗时间"></el-table-column>
        <el-table-column prop="addr" label="诊疗机构"></el-table-column>
        <el-table-column prop="addr" label="诊疗结果"></el-table-column>
      </el-table-column>
      <el-table-column label="接触人员情况">
        <el-table-column prop="addr" label="姓名"></el-table-column>
        <el-table-column prop="addr" label="性别"></el-table-column>
        <el-table-column prop="addr" label="年龄"></el-table-column>
        <el-table-column prop="addr" label="现住地"></el-table-column>
        <el-table-column prop="addr" label="电话"></el-table-column>
      </el-table-column>
    </el-table>
    <!-- 分页 -->
    <div class="pagination">
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page.sync="currentPage"
        :page-size="100"
        layout="total, prev, pager, next"
        :total="1000"
      ></el-pagination>
    </div>
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
      detailArr: [],

      // 分页
      currentPage: 1
    };
  },
  methods: {
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    // 切换分页
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    },

    // 进行查询
    getFilterSearch() {}
  },
  mounted() {}
};
</script>

<style scoped lang="scss">
.pagination {
  display: flex;
  justify-content: flex-end;
  margin-top: 20px;
}
</style>