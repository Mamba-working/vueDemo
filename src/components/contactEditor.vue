<template>
   <div>
    <h2>联系方式</h2>

    <el-form>    

          <el-form-item v-for="(key,index) in keys" :key="index">
           <span>{{lables[key]}}</span>
          <el-input  v-model="items[key]"></el-input>
          </el-form-item>
          
     
         
    </el-form-item>

   </el-form>
   </div>
</template>


<script>
    export default{
    props:["items","lables"],
    computed:{
      keys(){
        return Object.keys(this.items)
      }
    }
    }
</script>