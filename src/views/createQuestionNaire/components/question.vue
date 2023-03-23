<template>
  <div>
    <div

      style="display: flex;flex-direction: column;border: 2px solid #d3d3f0;width: 700px;padding: 20px;"
    >
      <div style="margin-bottom: 20px;display: flex;justify-content: space-between;">
        .请编辑问题?  【 填空 】
        <div>
          <el-button size="mini" type="primary" @click="toTop">上移</el-button>
          <el-button size="mini" type="primary">下移</el-button>
          <el-button size="mini" type="primary">编辑</el-button>
          <el-button size="mini" type="primary">删除</el-button>
        </div>
      </div>

      <textarea cols="80" rows="5" />
      <div v-if="show" style="display: flex;justify-content: center;margin-top: 10px;">
        <el-button style="width:350px">取消编辑</el-button>
        <el-button type="primary" style="width:350px">完成编辑</el-button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Question',
  components: {},
  props: {
  },
  data() {
    return {
      flag: false
    }
  },
  created() {},
  mounted() {},
  methods: {
    // edit() {
    //   this.flag = true
    // }
    toTop() {
      this.$emit('top')
    }

  }
}
</script>

<style lang="scss" scoped>

</style>
