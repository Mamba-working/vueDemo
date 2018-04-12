<template>
  <div id="edit">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active:currentTab === i}" v-on:click="currentTab = i">
          <svg class="icon">
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>

      </ol>
    </nav>
    <ol>
      <li v-bind:class="{active:currentTab === 0}">
        <contac v-bind:items="profile" v-bind:lables="{ name:'姓名' ,age:'年龄' ,school:'学校' ,city:'城市' ,}"/>
      </li>
      <li v-bind:class="{active:currentTab === 1}">
        <workHistoryEditor v-bind:workHistory="workHistory" />

      </li>
      <li v-bind:class="{active:currentTab === 2}">
        <studyHistoryEditor v-bind:studyHistory="studyHistory" />
      </li>
      <li v-bind:class="{active:currentTab === 3}">
        <project-history v-bind:projectHistory="projectHistory"/>
      </li>
      <li v-bind:class="{active:currentTab === 4}">
       <prize-history v-bind:prizeHistory="projectHistory"/>
      </li>
      <li v-bind:class="{active:currentTab === 5}">
        <contac v-bind:items="contac" v-bind:lables="{'phone':'电话','email':'邮箱','qq':'qq'}"/>
      </li>
    </ol>
  </div>
</template>
<script>
  import workHistoryEditor from "./workHistoryEditor"
  import studyHistoryEditor from "./studyHistoryEditor"
  import projectHistory from "./projectEditor.vue"
  import prizeHistory from "./prizeHistory.vue"
  import contac from "./contactEditor.vue"
  export default {
    components: {
      workHistoryEditor,
      studyHistoryEditor,
      projectHistory,
      prizeHistory,
      contac
    },
    data() {
      return {
        currentTab: 0,
        icons: ["shenfenzheng", "work", "book", "heart", "goldcup", "phone"],
        profile: {
          name: "",
          age: "",
          school: "",
          city: "",
        },
        workHistory: [{
          company: '',
          duration:'',
          workContent: '',
          
        }],
        studyHistory: [{
          school: '',
          duration: '',
          degree: ''
        }],
        projectHistory:[{
            name:'',
            duration:'',
            address:''
        }],
        prizeHistory:[{
            name:'',
            time:'',
            decribe:''
        }],
        contac:{
            phone:"",
            email:"",
            qq:""
        }
      }
    },
    
  }

</script>
<style lang="scss">
  #edit {
    min-height: 100px;
    display: flex;
    nav {
      background: #409EF6;
      width: 80px;
      >ol {
        display: flex;
        flex-direction: column;
        height: 100%;
        box-shadow: 0 0 3px rgba(0, 0, 0, 0.5);
        >li {
          cursor: pointer;
          display: flex;
          flex: 1;
          padding: 8px 0;
          width: 100%;
          align-items: center;
          justify-content: center;

          >.icon {
            width: 24px;
            height: 24px;
            fill: white;
          }
          &.active {
            background: white;
            >.icon {
              fill: black;
            }
          }
        }
      }

    }
    >ol {
      overflow: auto;
      flex: 1;
      position: relative;
      >li {
        padding: 32px;
        display: none;
        &.active {
          display: block;
        }
        .el-form>div {
          position: relative;
          .el-button--danger {
            position: absolute;
            right: 0;
            top: 0;
          }
        }
      }
    }
  }

</style>
