<template>
  <v-col cols="12" md="6" class="DataCard">
    <severe-case-bar-chart
      :title="$t('マスク着用率(大阪市)')"
      title-id="positive-status-severe-case3"
      chart-id="time-bar-chart-positive-status-severe-case3"
      :chart-data="graphData"
      :date="Data.date"
      unit="%"
    >
      <template v-slot:additionalDescription>
        <ul>
          <li>
            {{ $t('（注）画像認識により自動でカウント') }}
          </li>
        </ul>
      </template>
    </severe-case-bar-chart>
  </v-col>
</template>

<script>
import Data from '@/data/mask_status_auto.json'
import SevereCaseBarChart from '@/components/SevereCaseBarChart.vue'

export default {
  components: {
    SevereCaseBarChart
  },
  data() {
    const graphData = []
    Data.data
      .filter(d => new Date(d.date) > new Date('2020-04-21'))
      .filter(d => d.city === 'jp_dotonbori_donki')
      .forEach(d => {
        const date = new Date(d.date)
        const subTotal = (d.mask / (d.mask + d.no_mask)) * 100
        if (!isNaN(subTotal)) {
          graphData.push({
            label: `${date.getMonth() + 1}/${date.getDate()}`,
            transition: subTotal
          })
        }
      })
    return {
      Data,
      graphData
    }
  }
}
</script>
