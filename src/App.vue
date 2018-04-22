<template>
  <div id="app">
    <div class="container">
      <HelloWorld/>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
  .dot{
    stroke: #000;
  }

  .label{
    display: block;
    font-size: 11px;
  }

  .tooltip{

    position: absolute;
    /*width: 250px;*/
    height: 70px;
    pointer-events: none;
  }

  text {
    display: block;
  }
</style>
