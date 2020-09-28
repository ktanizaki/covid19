<template>
  <v-col cols="12" md="6" class="DataCard">
    <severe-case-bar-chart
      :title="$t('マスク着用率(ヴェネツィア)')"
      title-id="positive-status-severe-case5"
      chart-id="time-bar-chart-positive-status-severe-case5"
      :chart-data="graphData"
      :date="Data.date"
      unit="%"
    >
      <template v-slot:additionalDescription>
        <div class="my-1">
          <v-btn small @click="updateData()">Update</v-btn>
        </div>
        <ul>
          <li>
            {{ $t('（注）計上を開始した*月**日から作成') }}
          </li>
        </ul>
      </template>
    </severe-case-bar-chart>
  </v-col>
</template>

<script>
import Data from '@/data/mask_status.json'
import SevereCaseBarChart from '@/components/SevereCaseBarChart.vue'

export default {
  components: {
    SevereCaseBarChart
  },
  data() {
    const graphData = []
    Data.data
      .filter(d => new Date(d.date) > new Date('2020-04-21'))
      .filter(d => d.city === 'it_venice_rialto_bridge')
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
  },
  mounted() {
    /*
    let axios = document.createElement('script')
    axios.setAttribute('src', 'https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js')
    document.head.appendChild(axios)
    */
  },
  methods: {
    // window:onload = function() {
    //  this.updateData();
    // },
    updateData() {
      console.log(this.graphData)
      /*
      let response
      axios.get("https://raw.githubusercontent.com/ktanizaki/covid19/development/data/mask_status.json").then(
        response => (
          response.data.data
            .filter(d => new Date(d.date) > new Date('2020-06-06'))
            .forEach(d => {
              console.log(this.graphData.length);
              console.log(this.graphData[this.graphData.length - 1].label);
              const date = new Date(d.date)
              const subTotal = (d.mask / (d.mask + d.no_mask)) * 100
              if (!isNaN(subTotal)) {
                this.graphData.push({
                  label: `${date.getMonth() + 1}/${date.getDate()}`,
                  transition: subTotal
                })
              }
            })
        )
      )
      console.log(this.graphData)
      */
    }
  }
}
</script>
