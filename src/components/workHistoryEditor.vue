<template>
  <div>
    <h2>工作经历</h2>
    <el-form>
      <div v-for="(item,index) in workHistory">
        <el-form-item label="公司名称">
          <el-input v-model="item.company"></el-input>
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
        <el-form-item label="工作内容">
          <el-input v-model="item.workContent"></el-input>
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
          workContent: '',
          duration: ''
        })
      },
      removeWork(index) {
       if (this.workHistory.length > 1) {
          this.workHistory.splice(index, 1)
        }

      }
    }
  }

</script>
