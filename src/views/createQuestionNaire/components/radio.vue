<template>
  <div>
    <div
      v-if="!show"
      style="display: flex;flex-direction: column;border: 2px solid #d3d3f0;width: 700px;align-self: center;padding: 20px;"
    >
      <div style="margin-bottom: 20px;display: flex;justify-content: space-between;">
        .请编辑问题?  【 单选 】
        <div>
          <el-button size="mini" type="primary">上移</el-button>
          <el-button size="mini" type="primary">下移</el-button>
          <el-button size="mini" type="primary" @click="showFlag">编辑</el-button>
          <el-button size="mini" type="primary" @click="delTab">删除</el-button>
        </div>
      </div>
      <div v-if="flag">
        <el-input v-model="textValue" type="textarea" placeholder="请在此输入问题" />
        <el-form size="mini" style="font-size: 12px;">
          <div v-for="(item,index) in formItems" :key="index">
            <el-form-item>
              <el-radio v-model="item.radio" />
              <el-input v-model="item.input" placeholder="[单选]" style="margin-left: -30px;" />
              <el-radio v-model="item.radio1" style="margin-left: 20px;">可填空</el-radio>
              <el-button type="danger" @click="delInput(item, index)">删除</el-button>
            </el-form-item>
          </div>
        </el-form>
        <el-button size="mini" style="margin-top: 10px;" @click="addChoose">增加选项</el-button>
        <div style="display: flex;justify-content: center;margin-top: 10px;">
          <el-button style="width:350px">取消编辑</el-button>
          <el-button type="primary" style="width:350px" @click="complete">完成编辑</el-button>
        </div>
      </div>
    </div>
    <div
      v-if="show"
      style="display: flex;flex-direction: column;border: 2px solid #d3d3f0;width: 700px;margin-left: 215px;padding: 20px;"
    >
      <div>{{ textValue }} [单选]</div>
      <div v-for="(item,index) in radioValue" :key="index">
        <el-radio>{{ item }}</el-radio>
      </div>

    </div>
  </div>
</template>

<script>

export default {
  name: 'Radio',
  components: {},
  props: {
  },
  data() {
    return {
      show: false,
      flag: false,
      textValue: '',
      formItems: [],
      radioValue: []
    }
  },
  created() {},
  mounted() { },
  methods: {
    // 增加选项
    addChoose() {
      this.formItems.push({ 'radio': '', 'input': '', 'radio1': '' })
      console.log(this.formItems)
    },
    showFlag() {
      this.flag = true
    },
    // 删除 按钮 删除增加的选项
    delInput(index) {
      this.formItems.splice(index, 1)
    },
    // 完成编辑 按钮
    complete() {
      this.show = true
      this.radioValue = this.formItems.map(e => e.input)
    },
    // 删除单选 选项卡
    delTab() {
      this.$emit('del')
    }
  }
}
</script>

<style lang="scss" scoped>
li{
    line-height: 40px;
}
li::marker{
    content:''
}
::v-deep .el-form-item--mini .el-form-item__content{
  display: flex !important;
  align-items: center !important;
  justify-content: center;
  margin-top: 10px;
}
</style>
