<script setup lang="ts">
// imported components
import ChartCards from '../../widgets/chart/components/ChartCards.vue';
import IncomeCompare from '../../widgets/chart/components/IncomeCompare.vue';
import SalesReport from '../../widgets/chart/components/SalesReport.vue';
import PageView from './components/PageView.vue';
import RecentOrder from '../default/components/RecentOrder.vue';
import AnalyticsReport from '../default/components/AnalyticsReport.vue';
import TransactionHistory from './components/TransactionHistory.vue';
// import HelpSupport from './components/HelpSupport.vue';
import TaskCard from '../../widgets/statistics/components/TaskCard.vue';
// import SkillCard from '../../widgets/statistics/components/SkillCard.vue';
import AcquisitionChannels from '../../widgets/chart/components/AcquisitionChannels.vue';
</script>

<template>
  <v-row class="mt-0">
    <!-- column 1 -->
    <!-- <v-col cols="12" class="pt-2">
      <WelcomeBanner />
    </v-col> -->

    <!-- column 2 -->
    <v-col cols="12" class="pb-0">
      <ChartCards />
    </v-col>

    <!-- column-3 -->
    <v-col cols="12" md="8">
      <IncomeCompare />
    </v-col>

    <!-- column 4 -->
    <v-col cols="12" md="4">
      <PageView />
    </v-col>

    <!-- column 5 -->
    <v-col cols="12" md="8">
      <RecentOrder />
    </v-col>

    <!-- column 6 -->
    <v-col cols="12" md="4">
      <AnalyticsReport />
    </v-col>

    <!-- column 7 -->
    <v-col cols="12" md="7">
      <!-- <v-row md="8">
        <SalesReport />
      </v-row>
      <v-row > 
        <TaskCard />
      </v-row> -->
      <v-row>
        <v-col cols="12">
          <SalesReport />
        </v-col>
        <v-col>
          <TaskCard />
        </v-col>
      </v-row>
    </v-col>

    <!-- column 8 -->
    <v-col cols="12" md="5">
      <v-row>
        <!-- -------------------------------------------------------------------- -->
        <!-- Transaction History -->
        <!-- -------------------------------------------------------------------- -->
        <v-col cols="12">
          <TransactionHistory />
        </v-col>
        <v-col>
          <AcquisitionChannels />
        </v-col>
        <!-- -------------------------------------------------------------------- -->
        <!-- Help support -->
        <!-- -------------------------------------------------------------------- -->
        <!-- <v-col cols="12">
          <HelpSupport />
        </v-col> -->
      </v-row>
    </v-col>

    <!-- column 10 -->
    <!-- <v-col cols="12" md="4">
      <AcquisitionChannels />
    </v-col> -->
  </v-row>
</template>
