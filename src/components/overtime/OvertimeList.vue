<template>

  <h1>加班记录</h1>

  <n-data-table
      :columns="dataInfo.columns"
      :data="dataInfo.dataList"
      :row-key="(row) => row.n"
  />

</template>

<script>
import { NDataTable } from 'naive-ui'
/**
 * 加班历史记录表格
 */
export default {
  name: "OvertimeList",
  components: { NDataTable } ,
  setup() {

    const yesOrNoRender = (colName) => {
      return (row) => {
        return row[colName] ? '是' : '否'
      }
    }

    return {
      dataInfo: {
        columns: [
          {
            title: '序号',
            key: 'n',
          }, {
            title: '企业',
            key: 'company',
            ellipsis: {
              tooltip: true
            }
          }, {
            title: '日期',
            key: 'date',
          }, {
            title: '开始时间',
            key: 'start_time',
          }, {
            title: '结束时间',
            key: 'end_time',
          }, {
            title: '时长(min)',
            key: 't_long',
          }, {
            title: '是否周末',
            key: 'weekend',
            render: yesOrNoRender('weekend')
          }, {
            title: '是否出差',
            key: 'business_trip',
            render: yesOrNoRender('business_trip')
          }, {
            title: '是否节假日',
            key: 'holiday',
            render: yesOrNoRender('holiday')
          }, {
            title: '备注',
            key: 'remark',
            ellipsis: {
              tooltip: true
            }
          }
        ],
        dataList2: [],
        dataList: [
          {
            n: 0,
            company: '传智专修学院有限公司',
            date: '2021-8-06',
            start_time: '2021-08-06 18:00:00',
            end_time: '2021-08-06 21:00:00',
            t_long: 3 * 60,
            weekend: true,
            business_trip: false,
            holiday: false,
            remark: '记忆是一片叶子, 带走了春天与微风。',
          },{
            n: 1,
            company: '传智专修学院有限公司',
            date: '2021-8-06',
            start_time: '2021-08-06 18:00:00',
            end_time: '2021-08-06 21:00:00',
            t_long: 3 * 60,
            weekend: true,
            business_trip: false,
            holiday: false,
            remark: '记忆是一片叶子, 带走了春天与微风。',
          },{
            n: 2,
            company: '传智专修学院有限公司',
            date: '2021-8-06',
            start_time: '2021-08-06 18:00:00',
            end_time: '2021-08-06 21:00:00',
            t_long: 3 * 60,
            weekend: true,
            business_trip: false,
            holiday: false,
            remark: '记忆是一片叶子, 带走了春天与微风。',
          },{
            n: 3,
            company: '传智专修学院有限公司',
            date: '2021-8-06',
            start_time: '2021-08-06 18:00:00',
            end_time: '2021-08-06 21:00:00',
            t_long: 3 * 60,
            weekend: true,
            business_trip: false,
            holiday: false,
            remark: '记忆是一片叶子, 带走了春天与微风。',
          },
        ]
      }

    }

  }
}
</script>

<style scoped>

</style>