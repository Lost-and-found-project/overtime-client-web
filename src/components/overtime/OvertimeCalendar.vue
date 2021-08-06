<template>
  <n-calendar
      @update:value="handleValueUpdate"
              :value="value"
              :is-date-disabled="isDateDisabled"
              #="{ year, month, date }">

    <div>
      <span>
        <span style="font-size: 18px">
          <b>
          {{ year + (month < 10 ? '-0' : '-') + month + (date < 10 ? '-0' : '-') + date }}
          </b>
        </span>
        <span style="padding-left: 10px;">
          <n-tag round size="small" type="info" >工作日</n-tag>
        </span>
      </span>



      <something-show :label="'工作时间'" :context="'8h'">
        <template #header>
          <n-icon :color="themeVars.infoColor">
            <Briefcase/>
          </n-icon>
        </template>
      </something-show>
      <something-show :label="'加班时间'" :context="'4h'">
        <template #header>
          <n-icon :color="themeVars.warningColor">
            <Clock/>
          </n-icon>
        </template>
      </something-show>
      <something-show :label="'已得补偿'" :context="'3.5h'">
        <template #header>
          <n-icon :color="themeVars.successColor">
            <Scales24Filled/>
          </n-icon>
        </template>
      </something-show>

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
        <something-show :label="'不需要补偿'">
          <template #header>
            <n-icon :color="themeVars.successColor">
              <CheckCircle/>
            </n-icon>
          </template>
        </something-show>
      </template>
    </div>

  </n-calendar>
</template>

<script>
import {
  useMessage,
  useThemeVars,
  NCalendar, NEllipsis, NDescriptions,
  NDescriptionsItem, NProgress, NIcon,
  NTag,
} from 'naive-ui'

import {CheckCircle, Briefcase, Clock} from '@vicons/fa'
import {Scales24Filled} from '@vicons/fluent'
import SomethingShow from "./SomethingShow.vue";

/**
 * 记录加班时间的日历
 *
 */
export default {
  // see https://www.naiveui.com/zh-CN/os-theme/components/calendar
  props: {
    value: Number,
    isDateDisabled: Function,
    overtimeData: Array // see OvertimeData
  },
  emits: ['update:value'],
  name: "OvertimeCalendar",
  components: {
    CheckCircle, Briefcase, Clock,
    Scales24Filled,
    SomethingShow,
    NCalendar, NEllipsis, NDescriptions,
    NDescriptionsItem, NProgress, NIcon,
    NTag,
  },
  setup(props, context) {
    const message = useMessage()
    return {
      themeVars: useThemeVars(),

      showType() {
        return Math.round(Math.random() * 2 + 1)
      },
      handleValueUpdate(timestamp, dateInfo) {
        const {year, month, date} = dateInfo
        message.info(year + (month < 10 ? '-0' : '-') + month + (date < 10 ? '-0' : '-') + date)
        context.emit('update:value', timestamp, dateInfo)
      }
    }
  },
}

function OvertimeData() {

}

</script>

<style scoped>
#app {
}
</style>