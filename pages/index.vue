<template>
  <div class="MainPage">
    <site-top-upper />
    <cards-tabs />
    <card-row class="DataBlock">
      <!-- モニタリング指標 -->
      <monitoring-status-overview-card />
      <!-- モニタリング指標 マスク着用率 -->
      <severe-case-card />
      <!-- モニタリング指標 マスク着用率2 -->
      <severe-case-card2 />
      <!-- モニタリング指標 マスク着用率3 -->
      <severe-case-card3 />
      <!-- モニタリング指標 マスク着用率4 -->
      <severe-case-card4 />
    </card-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import CardsTabs from '@/components/CardsTabs.vue'
import CardRow from '@/components/cards/CardRow.vue'
import SevereCaseCard from '@/components/cards/SevereCaseCard.vue'
import SevereCaseCard2 from '@/components/cards/SevereCaseCard2.vue'
import SevereCaseCard3 from '@/components/cards/SevereCaseCard3.vue'
import SevereCaseCard4 from '@/components/cards/SevereCaseCard4.vue'
import MonitoringStatusOverviewCard from '@/components/cards/MonitoringStatusOverviewCard.vue'

export default Vue.extend({
  components: {
    CardsTabs,
    CardRow,
    SevereCaseCard,
    SevereCaseCard2,
    SevereCaseCard3,
    SevereCaseCard4,
    MonitoringStatusOverviewCard
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
