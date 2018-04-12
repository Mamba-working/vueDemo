<template>
  <div>
    <h2>工作经历</h2>
    <el-form>
      <div v-for="(work,index) in workHistory">
        <el-form-item label="公司名称">
          <el-input v-model="work.company"></el-input>
        </el-form-item>
        <el-form-item label="工作内容">
          <el-input v-model="work.workContent"></el-input>
        </el-form-item>
        <el-button type="danger" icon="el-icon-delete" circle size="mini" v-on:click="removeWork(index)"></el-button>
      </div>
    </el-form>
    <el-button type="primary" round v-on:click="addCompany">增加</el-button>
  </div>

</template>
<script>
  export default {
    props: ["workHistory"],
    methods: {
      addCompany() {
        this.workHistory.push({
          company: '',
          workContent: ''
        })
      },
      removeWork(index) {
        if (index > 0) {
          this.workHistory.splice(index, 1)
        }

      }
    }
  }

</script>
