<template>

  <h1>加班记录</h1>

  <n-data-table
      :columns="dataInfo.columns"
      :data="dataInfo.dataList"
      :row-key="(row) => row.n"
  />

</template>

<script>
import {NDataTable} from 'naive-ui'
import {ref} from "vue";
import overtimeDataList from "./OvertimeDataList.js";

/**
 * 加班历史记录表格
 */
export default {
  name: "OvertimeList",
  components: {NDataTable},
  setup() {
    const { dataInfo } = overtimeDataList()
    return {
      dataInfo: dataInfo
    }

  }
}
</script>