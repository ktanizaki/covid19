<template>
  <v-col cols="12" md="6" class="DataCard">
    <data-view
      :title="$t('モニタリング指標')"
      title-id="monitoring-status-overview"
      :date="monitoringStatusData.date"
    >
      <template v-slot:additionalDescription>
        <ul>
          <li>
            {{ $t('※') }}
          </li>
        </ul>
      </template>
      <monitoring-status-overview-table
        :aria-label="$t('モニタリング指標')"
        :status="monitoringStatus"
      />
    </data-view>
  </v-col>
</template>

<script>
import monitoringStatusData from '@/data/monitoring_status.json'
import formatMonitoringStatus from '@/utils/formatMonitoringStatus'
import DataView from '@/components/DataView.vue'
import MonitoringStatusOverviewTable from '@/components/MonitoringStatusOverviewTable.vue'

export default {
  components: {
    DataView,
    MonitoringStatusOverviewTable
  },
  data() {
    // モニタリング指標
    const monitoringStatus = formatMonitoringStatus(monitoringStatusData.data)

    return {
      monitoringStatusData,
      monitoringStatus
    }
  }
}
</script>
