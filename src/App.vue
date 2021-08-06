<template>
    {{ value == null ? 'null' : value }}
    <n-layout position="absolve" :native-scrollbar="false">
      <n-layout-header position="absolve">
        <div style="padding: 15px 15px 15px 15px;">
          <n-row>
            <n-col :span="12">
              <n-statistic label="统计数据" :value="99">
                <template #prefix>
                  @
                </template>
                <template #suffix>/ 100</template>
              </n-statistic>
            </n-col>
            <n-col :span="12">
              <n-statistic label="活跃用户">1,234,123</n-statistic>
            </n-col>
          </n-row>
        </div>
      </n-layout-header>

      <n-divider/>

      <n-layout-content>
        <n-layout :native-scrollbar="false"
                  style="padding: 15px 15px 15px 15px;">
          <n-message-provider>
            <overtime-calendar
                v-model:value="value"
                :is-date-disabled="isDate"/>
          </n-message-provider>
        </n-layout>
        <!--                @update:value="onUp" -->

        <n-layout style="padding: 15px 15px 15px 15px;">
          <n-message-provider>
            <overtime-list/>
          </n-message-provider>
        </n-layout>
      </n-layout-content>


    </n-layout>


  <!--6666-->
</template>

<script>
// https://www.naiveui.com/zh-CN/os-theme/components/message
import {NMessageProvider, NLayout, NRow, NCol, NStatistic, NDivider} from 'naive-ui'
import OvertimeCalendar from "./components/overtime/OvertimeCalendar.vue";
import OvertimeList from "./components/overtime/OvertimeList.vue";
import {ref} from "vue";

export default {
  components: {
    OvertimeList, OvertimeCalendar,
    NMessageProvider, NLayout, NRow, NCol, NStatistic, NDivider
  },
  name: "App",
  setup() {
    return {
      value: ref(null),
      onUp(time, {year, month, date}) {
        console.log('onUp(time, { ' + year + ', ' + month + ' , ' + date + '})')
      },
      isDate(t) {
        return true
      }
    }
  },
  methods: {}
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
