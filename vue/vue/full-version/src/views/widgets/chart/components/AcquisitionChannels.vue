<script setup lang="ts">
import { computed, shallowRef } from 'vue';
import { useTheme } from 'vuetify';
import { getPrimary, getLightPrimary } from '../../../forms/charts/apex-chart/UpdateColors';
// import icons
import { FundProjectionScreenOutlined, FileTextOutlined } from '@ant-design/icons-vue';

const theme = useTheme();
const DarkColor = theme.current.value.colors.darkText;

const chartOptions1 = computed(() => {
  return {
    chart: {
      type: 'bar',
      height: 250,
      fontFamily: `inherit`,
      foreColor: '#a1aab2',
      stacked: true,
      toolbar: {
        show: false
      }
    },
    dataLabels: {
      enabled: false
    },
    plotOptions: {
      bar: {
        columnWidth: '90%'
      }
    },
    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
    colors: [DarkColor, getPrimary.value, getLightPrimary.value],
    stroke: {
      curve: 'smooth',
      width: 6,
      colors: ['transparent']
    },
    fill: {
      opacity: 1
    },
    legend: {
      position: 'bottom',
      horizontalAlign: 'left',
      offsetX: -10,
      markers: {
        width: 8,
        height: 8,
        radius: 12
      }
    },
    yaxis: {
      labels: {
        show: false
      }
    },
    xaxis: {
      labels: {
        show: false
      },
      axisBorder: {
        show: false
      },
      axisTicks: {
        show: false
      }
    },
    grid: {
      show: false
    },
    tooltip: {
      fixed: {
        enabled: false
      },
      x: {
        show: false
      }
    }
  };
});

// chart 1
const barChart1 = {
  series: [
    {
      name: '直接搜索',
      data: [21, 17, 15, 13, 15, 13, 16, 13, 8, 14, 11, 9, 7, 5, 3, 3, 7]
    },
    {
      name: '转介',
      data: [28, 30, 20, 26, 18, 27, 22, 28, 20, 21, 15, 14, 12, 10, 8, 18, 16]
    },
    {
      name: '社会渠道',
      data: [50, 51, 60, 54, 53, 48, 55, 40, 44, 42, 44, 44, 42, 40, 42, 32, 16]
    }
  ]
};

const channels = shallowRef([
  {
    color: 'light',
    icon: FundProjectionScreenOutlined,
    name: '热门频道',
    time: '今天, 8:00 上午',
    price: '+ 30⭐',
    percent: '7.1%'
  },
  {
    color: 'primary',
    icon: FileTextOutlined,
    name: '热门网页',
    time: '今天, 16:00 下午',
    price: '- 128⭐',
    percent: '-10.6%'
  }
]);
</script>

<template>
  <v-card class="title-card" variant="text" rounded="md">
    <v-card-text variant="outlined" class="rounded-md pa-0">
      <div class="pt-5 d-flex align-center px-4">
        <div>
          <h6 class="text-subtitle-1 mb-0">客户获取渠道</h6>
          <span class="text-caption text-lightText mb-0">营销</span>
        </div>
        <h5 class="text-primary text-h5 ml-auto">-128</h5>
      </div>
      <apexchart type="bar" height="250" :options="chartOptions1" :series="barChart1.series"> </apexchart>

      <v-list class="py-0" lines="two" aria-label="channel list" aria-busy="true" border>
        <v-list-item v-for="(page, i) in channels" :key="i" :value="page" rounded="sm" color="secondary" class="no-spacer">
          <template v-slot:prepend>
            <v-avatar size="36" :color="page.color" variant="tonal" class="mr-3 py-2">
              <component :is="page.icon" :style="{ fontSize: '16px' }" />
            </v-avatar>
          </template>
          <div class="d-inline-flex align-center justify-space-between w-100">
            <div>
              <h6 class="text-subtitle-1 mb-0">{{ page.name }}</h6>
              <p class="text-caption text-lightText mb-0">{{ page.time }}</p>
            </div>
            <div class="text-right">
              <h6 class="text-subtitle-1 mb-0">{{ page.price }}</h6>
              <span class="text-h6 text-lightText">
                {{ page.percent }}
              </span>
            </div>
          </div>
        </v-list-item>
      </v-list>
    </v-card-text>
  </v-card>
</template>
