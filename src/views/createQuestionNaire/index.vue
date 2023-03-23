<template>
  <div>
    <el-card>
      <div class="input" style="display: flex;justify-content: center;">
        <div style="border-bottom :1px solid #ccc;" />
        <el-input v-model="title" style="width:400px" placeholder="请在这里输入问卷标题" />
      </div>
      <div v-for="(item,index) in items" :key="index" style="display: flex;align-items: center;flex-direction: column;">
        <div :is="item.component" @del="delComponent(index)" />
      </div>
      <el-form ref="ruleForm" class="choose" style="display: flex; justify-content: center;margin:20px 0 0 40px;" size="mini" :model="ruleForm" :rules="rules">
        <div style="margin: 6px 5px 0 0;font-size: 12px;">截止时间: </div>
        <el-form-item style="margin: 0 5px;" prop="date">
          <el-date-picker v-model="ruleForm.date" type="date" placeholder="选择日期" style="width: 200px;" />
        </el-form-item>
        <el-form-item style="margin: 0 5px">
          <el-select v-model="ruleForm.cate" placeholder="问卷类别">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            />
          </el-select>
        </el-form-item>
        <el-form-item style="margin: 0 5px;">
          <el-select v-model="ruleForm.quest" placeholder="添加问题">
            <el-option
              v-for="item in options1"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            />
          </el-select>
        </el-form-item>
        <el-form-item>
          <el-button type="success" @click="pushQuestion('ruleForm')">发布</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
import question from '@/views/createQuestionNaire/components/question.vue'
import radio from '@/views/createQuestionNaire/components/radio.vue'
export default {
  name: '',
  components: {
    question,
    radio
  },
  props: {
  },
  data() {
    return {
      title: '',
      items: [],
      options: [{
        value: '选项1',
        label: 'A类'
      }, {
        value: '选项2',
        label: 'B类'
      }, {
        value: '选项3',
        label: 'C类'
      }, {
        value: '选项4',
        label: 'D类'
      }, {
        value: '选项5',
        label: 'E类'
      }],

      options1: [{
        value: '单选',
        label: '单选'
      }, {
        value: '多选',
        label: '多选'
      }, {
        value: '填空',
        label: '填空'
      }],
      cate: '',
      quest: '',
      ruleForm: {
        date1: '',
        cate: '',
        quest: ''
      },
      rules: {
        data1: [
          { require: true, message: '请选择截止日期', trigger: 'change' }
        ],
        cate: [
          { require: true, message: '请选择问卷类别', trigger: 'change' }
        ],
        quest: [
          { require: true, message: '请选择添加问题', trigger: 'change' }
        ] }

    }
  },
  created() {},
  mounted() {},
  methods: {
    pushQuestion(formName) {
      if (this.quest === '填空') {
        this.items.push({
          'component': question
        })
      } else if (this.quest === '单选') {
        this.items.push({
          'component': radio
        })
      }
    },
    delComponent(index) {
      this.items.splice(index, 1)
    }
  }

}
</script>

<style lang="scss" scoped>

</style>
