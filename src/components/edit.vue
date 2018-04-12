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
            <profileEditor v-bind:profile="profile"/>
      </li>
      <li v-bind:class="{active:currentTab === 1}">
       <workHistoryEditor v-bind:workHistory="workHistory"/>

      </li>
      <li v-bind:class="{active:currentTab === 2}">
        <h2>学习经历</h2>
      </li>
      <li v-bind:class="{active:currentTab === 3}">
        <h2>项目经验</h2>
      </li>
      <li v-bind:class="{active:currentTab === 4}">
        <h2>
          奖项
        </h2>
      </li>
      <li v-bind:class="{active:currentTab === 5}">
        <h2>联系方式</h2>
      </li>
    </ol>
  </div>
</template>
<script>
import profileEditor from "./profileEditor"
import workHistoryEditor from "./workHistoryEditor"
  export default {
      components:{
          profileEditor,
          workHistoryEditor
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
          workContent: ''
        }]
      }
    },
    methods: {

    }
  }

</script>
<style lang="scss">
  #edit {
    min-height: 100px;
    display: flex;
    nav {
      background: black;
      width: 80px;
      >ol {
        display: flex;
        flex-direction: column;
        height: 100%;

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
