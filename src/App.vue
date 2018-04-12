<template>
  <div id="app">
    <Topbar class="topbar"/>
    <main>
  <Edit class="edit"/>
     <Preview class="preview"/>
    </main>
   
  </div>
</template>

<script>
import Topbar from './components/topbar'
import Edit from './components/edit'
import Preview from './components/preview'
export default {
  
  components: {
   Topbar,
   Edit,
   Preview
  }
}
</script>

<style lang="scss">
 .icon {
       width: 1em; height: 1em;
       vertical-align: -0.15em;
       fill: currentColor;
       overflow: hidden;
    }
#app{
  display: flex;
  flex-direction: column;
  height: 100vh;
}
.topbar{
   box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
   position: relative;
   z-index: 1;
}
main{
  flex:1;
  background: #eee;
  display: flex;
>.edit{
  width:40em;
  margin:16px 8px 16px 16px;
  background: white;
  box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
  border-radius: 5px;
  overflow:hidden;
}
>.preview{
  flex:1;
  margin: 16px 16px 16px 8px;
  background: white;
  box-shadow: 0 0 3px hsla(0, 0, 0, 0.5);
  border-radius: 5px;
}
}

</style>
