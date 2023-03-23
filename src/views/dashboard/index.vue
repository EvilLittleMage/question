<template>
  <div class="dashboard-container">
    <el-card>
      <div class="header" style="height:200px;background: url('http://www.zjxz.edu.cn/_upload/site/00/06/6/logo.jpg') no-repeat;center;background-size:100% 200px;display: flex;justify-content:space-around">
        <h2 class="title" style="margin-top: 10px;color: #fff;margin-left: 320px;">在线问卷调查系统</h2>
        <div class="btnGrounp" style="margin-top: 10px;">
          <el-button>个人中心</el-button>
          <el-button @click="gotoCreat">创建问卷</el-button>
        </div>
      </div>
      <el-table
        :data="tableData"
        style="width: 100%"
      >
        <el-table-column
          prop="date"
          label="问卷名称"
          width="180"
        />
        <el-table-column
          prop="name"
          label="问卷类型"
          width="180"
        />
        <el-table-column
          prop="address"
          label="截止时间"
        />
        <el-table-column
          prop="address"
          label="问卷操作"
        />
      </el-table>
    </el-card>
  </div>
</template>

<script>

import { mapGetters } from 'vuex'
// import adminDashboard from './admin'
// import editorDashboard from './editor'

export default {
  name: 'Dashboard',
  // components: { adminDashboard, editorDashboard },
  data() {
    return {
      currentRole: 'adminDashboard',
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1517 弄'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1519 弄'
      }, {
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1516 弄'
      }]
    }
  },
  computed: {
    ...mapGetters([
      'roles'
    ])
  },
  created() {
    if (!this.roles.includes('admin')) {
      this.currentRole = 'editorDashboard'
    }
  }, methods: {
    gotoCreat() {
      this.$router.push('/createQuestionNaire/index')
    }
  }
}
</script>
