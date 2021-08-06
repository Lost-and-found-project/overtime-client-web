<template>
  <n-message-provider>

    <overtime-calendar @update:value="onUp" :is-date-disabled="isDate" />

  </n-message-provider>
</template>

<script>
import OvertimeCalendar from "./components/overtime/OvertimeCalendar.vue";
// https://www.naiveui.com/zh-CN/os-theme/components/message
import { NMessageProvider } from 'naive-ui'

export default {
  components: {OvertimeCalendar, NMessageProvider},
  name: "App",
  setup() {
    return {
      onUp(time, { year, month, date }) {
        console.log('onUp(time, { '+ year +', '+ month +' , '+ date +'})')
      },
      isDate(t) {
        return true
      }
    }
  },
  methods: {

  }
}

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/master/active-rfcs/0040-script-setup.md
</script>

<style>
/*#app {*/
/*  font-family: Avenir, Helvetica, Arial, sans-serif;*/
/*  -webkit-font-smoothing: antialiased;*/
/*  -moz-osx-font-smoothing: grayscale;*/
/*  text-align: center;*/
/*  color: #2c3e50;*/
/*  margin-top: 60px;*/
/*}*/
</style>
