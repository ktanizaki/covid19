<template>
  <div class="MainPage">
    <site-top-upper />
    <cards-tabs />
    <card-row class="DataBlock">
      <!-- モニタリング指標 -->
      <!-- <monitoring-status-overview-card /> -->
      <!-- モニタリング指標 マスク着用率2 渋谷区 -->
      <severe-case-card2 />
      <!-- モニタリング指標 マスク着用率3 大阪市 -->
      <severe-case-card3 />
      <!-- モニタリング指標 マスク着用率4 台北 -->
      <severe-case-card4 />
      <!-- モニタリング指標 マスク着用率5 ヴェネチア -->
      <severe-case-card5 />
      <!-- モニタリング指標 マスク着用率6 ロンドン -->
      <severe-case-card6 />
      <!-- モニタリング指標 マスク着用率7 ダブリン -->
      <severe-case-card7 />
    </card-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import CardsTabs from '@/components/CardsTabs.vue'
import CardRow from '@/components/cards/CardRow.vue'
import SevereCaseCard2 from '@/components/cards/SevereCaseCard2.vue'
import SevereCaseCard3 from '@/components/cards/SevereCaseCard3.vue'
import SevereCaseCard4 from '@/components/cards/SevereCaseCard4.vue'
import SevereCaseCard5 from '@/components/cards/SevereCaseCard5.vue'
import SevereCaseCard6 from '@/components/cards/SevereCaseCard6.vue'
import SevereCaseCard7 from '@/components/cards/SevereCaseCard7.vue'
//import MonitoringStatusOverviewCard from '@/components/cards/MonitoringStatusOverviewCard.vue'

export default Vue.extend({
  components: {
    CardsTabs,
    CardRow,
    SevereCaseCard2,
    SevereCaseCard3,
    SevereCaseCard4,
    SevereCaseCard5,
    SevereCaseCard6,
    SevereCaseCard7
    //MonitoringStatusOverviewCard
  }
})
</script>

<style lang="scss" scoped>
.MainPage {
  .DataBlock {
    margin: 20px -8px;

    .DataCard {
      @include largerThan($medium) {
        padding: 10px;
      }

      @include lessThan($small) {
        padding: 4px 8px;
      }
    }
  }
}
</style>
