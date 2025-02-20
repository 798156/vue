<script setup lang="ts">
import { shallowRef } from 'vue';
// common components
import UiTitleCard from '@/components/shared/UiTitleCard.vue';

// icons
import { CheckOutlined, CloseOutlined, ClockCircleOutlined } from '@ant-design/icons-vue';

const transaction = shallowRef([
  {
    icon: CheckOutlined,
    subtitle: '今天  2:00 上午',
    title: '付款来自 : 002434',
    color: 'success',
    price: '+ ￥1430',
    pricepercent: '35%'
  },
  {
    icon: CloseOutlined,
    subtitle: '今天 6:00 上午',
    title: '订单退回来自 : 002434',
    color: 'error',
    price: '- ￥742',
    pricepercent: '-7.2%'
  },
  {
    icon: ClockCircleOutlined,
    subtitle: '今天 2:00 上午',
    title: '订单核验中 : 002554',
    color: 'primary',
    price: ' ￥2430',
    pricepercent: '11.3%'
  }
]);
</script>
<template>
  <UiTitleCard title="交易记录" class-name="px-0 pb-0 rounded-md overflow-hidden">
    <v-list lines="two" class="py-0" aria-label="transaction list" aria-busy="true">
      <v-list-item v-for="history in transaction" :key="history.title" :value="history.title" border>
        <template v-slot:prepend>
          <v-avatar size="36" :color="history.color" :class="`text-${history.color}`" variant="tonal">
            <component :is="history.icon" :style="{ fontSize: '16px' }" />
          </v-avatar>
        </template>
        <div class="d-flex align-center justify-space-between w-100 ga-2">
          <div>
            <h6 class="text-subtitle-1 mb-0">{{ history.title }}</h6>
            <span class="text-subtitle-2 text-lightText font-weight-regular">{{ history.subtitle }}</span>
          </div>
          <div class="text-right">
            <h6 class="text-subtitle-1 mb-0">{{ history.price }}</h6>
            <span class="text-h6 text-lightText">{{ history.pricepercent }}</span>
          </div>
        </div>
      </v-list-item>
    </v-list>
  </UiTitleCard>
</template>
