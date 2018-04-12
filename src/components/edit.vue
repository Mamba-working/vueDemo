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
      <li v-bind:class="{active:currentTab === 0}">1</li>
      <li v-bind:class="{active:currentTab === 1}">2</li>
      <li v-bind:class="{active:currentTab === 2}">3</li>
      <li v-bind:class="{active:currentTab === 3}">4</li>
      <li v-bind:class="{active:currentTab === 4}">5</li>
      <li v-bind:class="{active:currentTab === 5}">6</li>
      <li v-bind:class="{active:currentTab === 6}">7</li>
    </ol>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        currentTab: 4,
        icons: ["shenfenzheng", "work", "book", "heart", "goldcup", "phone"]
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
      >li {
        display: none;
        &.active {
          display: block;
        }
      }
    }
  }

</style>
