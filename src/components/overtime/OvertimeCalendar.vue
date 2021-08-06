<template>
  <n-calendar @update:value="handleValueUpdate"
              :is-date-disabled="isDateDisabled"
              #="{ year, month, date }">
    <div>
      <n-descriptions :column="1" :label-placement="'left'"
                      :title="year + (month < 10 ? '-0' : '-') + month + (date < 10 ? '-0' : '-') + date">
        <n-descriptions-item label="工作时间"> 8h</n-descriptions-item>
        <n-descriptions-item label="加班时间"> 4h</n-descriptions-item>
        <n-descriptions-item label="已得补偿"> 3.5h</n-descriptions-item>
      </n-descriptions>

      <template v-if="showType() === 1">
        <p>
          <n-progress :status="'warning'" :percentage="(3.5 / 4.0) * 100"></n-progress>
        </p>
      </template>
      <template v-else-if="showType() === 2">
        <p>
          <n-progress :status="'success'" :percentage="100"></n-progress>
        </p>
      </template>
      <template v-else>
        <p>
          <span> 不需要补偿喔 </span> &nbsp;
          <n-icon :color="themeVars.successColor">
            <CheckCircle />
          </n-icon>
        </p>
      </template>



    </div>
  </n-calendar>
</template>

<script>
import {
  useMessage,
  useThemeVars,
  NCalendar, NEllipsis, NDescriptions, NDescriptionsItem, NProgress, NIcon
} from 'naive-ui'

import { CheckCircle } from '@vicons/fa'

/**
 * 记录加班时间的日历
 *
 */
export default {
  // see https://www.naiveui.com/zh-CN/os-theme/components/calendar
  props: ['isDateDisabled'],
  emits: ['update:value'],
  name: "OvertimeCalendar",
  components: {CheckCircle,
    NCalendar, NEllipsis, NDescriptions, NDescriptionsItem, NProgress, NIcon},
  setup (props, context) {
    const message = useMessage()
    return {
      themeVars: useThemeVars(),

      showType() {
        return Math.round(Math.random()*2+1)
      },
      handleValueUpdate(timestamp, dateInfo) {
        const { year, month, date } = dateInfo
        message.info(year + (month < 10 ? '-0' : '-') + month + (date < 10 ? '-0' : '-') + date)
        context.emit('update:value', timestamp, dateInfo)
      }
    }
  },
  methods: {

  }
}

</script>

<style scoped>
#app {
}
</style>