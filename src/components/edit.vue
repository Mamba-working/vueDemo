<template>
  <div id="edit">
    <nav>
      <ol>
        <li v-for="i in [0,1,2,3,4,5]" v-bind:class="{active:currentTab === i}" v-on:click="currentTab = i">
          <svg class="icon">
            <use v-bind:xlink:href="`#icon-${icons[i]}`"></use>
          </svg>
        </li>
        <!-- <li v-bind:class="{active:currentTab === 0}" v-on:click="currentTab =0">
          <svg class="icon">
            <use xlink:href="#icon-shenfenzheng"></use>
          </svg>
        </li>
        <li v-bind:class="{active:currentTab === 1}" v-on:click="currentTab =1">
          <svg class="icon">
            <use xlink:href="#icon-phone"></use>
          </svg>
        </li>
        <li v-bind:class="{active:currentTab === 2}" v-on:click="currentTab =2">
          <svg class="icon">
            <use xlink:href="#icon-goldcup"></use>
          </svg>
        </li>
        <li v-bind:class="{active:currentTab === 3}" v-on:click="currentTab =3">
          <svg class="icon">
            <use xlink:href="#icon-book"></use>
          </svg>
        </li>
        <li v-bind:class="{active:currentTab === 4}" v-on:click="currentTab =4">
          <svg class="icon">
            <use xlink:href="#icon-heart"></use>
          </svg>
        </li>
        <li v-bind:class="{active:currentTab === 5}" v-on:click="currentTab =5">
          <svg class="icon">
            <use xlink:href="#icon-work"></use>
          </svg>
        </li> -->
      </ol>
    </nav>
    <ol>
      <li v-bind:class="{active:currentTab === 0}">
        <h2>个人信息</h2>
        <el-form>
          <el-form-item label="姓名">
            <el-input v-model="profile.name"></el-input>
          </el-form-item>
          <el-form-item label="年龄">
            <el-input v-model="profile.age"></el-input>
          </el-form-item>
          <el-form-item label="学校">
            <el-input v-model="profile.school"></el-input>
          </el-form-item>
          <el-form-item label="城市">
            <el-input v-model="profile.city"></el-input>
          </el-form-item>
        </el-form>
      </li>
      <li v-bind:class="{active:currentTab === 1}">
        <h2>工作经历</h2>
        <el-form>
          <div v-for="(work,index) in workHistory">
            <el-form-item label="公司名称">
              <el-input v-model="work.company"></el-input>
            </el-form-item>
            <el-form-item label="工作内容">
              <el-input v-model="work.workContent"></el-input>
            </el-form-item>
            <el-button type="danger" icon="el-icon-delete" circle size="small" v-on:click="removeWork(index)"></el-button>
          </div>
        </el-form>
        <el-button type="primary" round v-on:click="addCompany">增加</el-button>

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
  export default {
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
            font-size: 16px;
          }
        }
      }
    }
  }

</style>
