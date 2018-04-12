<template>
  <div>
    <h2>项目经验</h2>
    <el-form>
      <div v-for="(item,index) in projectHistory">
        <el-form-item label="项目名称">
          <el-input v-model="item.name"></el-input>
        </el-form-item>
        <el-form-item>
          <!-- <el-input v-model="item.duration"></el-input> -->
          <span class="demonstration">项目时间</span>
          <div class="block">

            <el-date-picker v-model="item.duration" type="daterange" align="right" unlink-panels range-separator="至" start-placeholder="开始日期"
              end-placeholder="结束日期" style="width:100%">
            </el-date-picker>
          </div>

        </el-form-item>
        <el-form-item label="预览地址">
          <el-input v-model="item.address"></el-input>
        </el-form-item>
        <el-button type="danger" icon="el-icon-delete" circle size="mini" v-on:click="removeitem(index)"></el-button>
      </div>
    </el-form>
    <el-button type="primary" round v-on:click="additem">增加</el-button>
  </div>
</template>

<script>
  export default {
    props: ["projectHistory"],
    methods: {
      additem() {
        this.projectHistory.push({
          name: '',
          duration: '',
          address: ''
        })
      },
      removeitem(index) {
        if (this.projectHistory.length > 1) {
          this.projectHistory.splice(index, 1)
        }

      }
    }
  }

</script>
