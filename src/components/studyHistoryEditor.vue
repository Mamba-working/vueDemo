<template>
  <div>
    <h2>学习经历</h2>
    <el-form>
      <div v-for="(item,index) in studyHistory">
        <el-form-item label="学校名称">
          <el-input v-model="item.school"></el-input>
        </el-form-item>
        <el-form-item>
          <!-- <el-input v-model="item.duration"></el-input> -->
         <span class="demonstration">时间</span>
          <div class="block">
            
        <el-date-picker
           v-model="item.duration"
           type="daterange"
           align="right"
           unlink-panels
           range-separator="至"
           start-placeholder="开始日期"
           end-placeholder="结束日期"
           style="width:100%"
         >
    </el-date-picker>
          </div>
          
        </el-form-item>
        <el-form-item label="学位">
          <el-input v-model="item.degree"></el-input>
        </el-form-item>
        <el-button type="danger" icon="el-icon-delete" circle size="mini" v-on:click="removeitem(index)"></el-button>
      </div>
    </el-form>
    <el-button type="primary" round v-on:click="additem">增加</el-button>
  </div>
</template>


<script>
  export default {
    props: ["studyHistory"],
    methods: {
      additem() {
        this.studyHistory.push({
          school: '',
          duration: '',
          degree: ''
        })
      },
      removeitem(index) {
        if (this.studyHistory.length > 1) {
          this.studyHistory.splice(index, 1)
        }

      }
    }
  }

</script>
