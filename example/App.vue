<template>
  <div class="main-wrap">
    <!--<button @click="pushTo('/')">
      button
    </button>
    <button @click="pushTo('/layout')">
      layout
    </button>
    <button @click="pushTo('/container')">
      container
    </button>
    <button @click="pushTo('/link')">
      Link
    </button>
    <button @click="pushTo('/radio')">
      radio
    </button>
    <button @click="pushTo('/form')">
      form
    </button>
    <button @click="pushTo('/input')">
      input
    </button>
    <button @click="pushTo('/inputNumber')">
      inputNumber
    </button>-->
    <el-button v-for="(item,index) in routes" :key="index" @click="pushTo(item.path)">
      {{item.name}}
    </el-button>
    <el-scrollbar class="components-page">
      <router-view style="padding: 15px"/>
    </el-scrollbar>
  </div>
</template>

<script>
  import {ref, onMounted} from 'vue'
  import {useRouter, useRoute} from 'vue-router'

  export default {
    setup(props, ctx) {
      const router = useRouter()
      const routes = ref(router.getRoutes())
      const pushTo = (path) => {
        router.push(path)
      }
      const root = ref(null)
      onMounted(() => {
        // console.log(root.value)
      })
      return {
        routes,
        pushTo,
        root
      }
    },
    mounted() {

    }
  }
</script>

<style lang="scss" scoped>
  .main-wrap {
    box-sizing: border-box;
    height: 100%;
  }

  img {
    width: 200px;
  }

  h1 {
    font-family: Arial, Helvetica, sans-serif;
  }
</style>
