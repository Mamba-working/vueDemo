<template>
  <div>
    <h2>获奖经验</h2>
    <el-form>
      <div v-for="(item,index) in prizeHistory">
        <el-form-item label="奖项">
          <el-input v-model="item.name"></el-input>
        </el-form-item>
        <el-form-item>
          <!-- <el-input v-model="item.duration"></el-input> -->
          <span class="demonstration">获奖时间</span>
          <div class="block">
            <el-date-picker v-model="prizeHistory.time" type="date" placeholder="选择日期">
            </el-date-picker>
          </div>

        </el-form-item>
        <el-form-item label="获奖描述">
          <el-input v-model="item.describe"></el-input>
        </el-form-item>
        <el-button type="danger" icon="el-icon-delete" circle size="mini" v-on:click="removeitem(index)"></el-button>
      </div>
    </el-form>
    <el-button type="primary" round v-on:click="additem">增加</el-button>
  </div>
</template>


<script>
export default{
    props:["prizeHistory"],
    methods:{
         additem() {
        this.prizeHistory.push({
          name: '',
          time: '',
          describe: ''
        })
      },
      removeitem(index) {
        if (this.prizeHistory.length > 1) {
          this.prizeHistory.splice(index, 1)
        }

      }
    }
    }


</script>
