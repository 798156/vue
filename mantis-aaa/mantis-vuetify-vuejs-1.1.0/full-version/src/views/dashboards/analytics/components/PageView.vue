<script setup lang="ts">
import { shallowRef } from 'vue';
// common components
import UiTitleCard from '@/components/shared/UiTitleCard.vue';

const transaction = shallowRef([
  {
    subtitle: '水果',
    title: '涌泉蜜桔',
    price: '775',
    pricepercent: '+31.74%'
  },
  {
    subtitle: '水果',
    title: '圣女果',
    price: '215',
    pricepercent: '+8.53%'
  },
  {
    subtitle: '蔬菜',
    title: '西兰花',
    price: '48',
    pricepercent: '-5.35%'
  },
  {
    subtitle: '农副产品',
    title: '梅干菜',
    price: '275',
    pricepercent: '+0.17%'
  },
  {
    subtitle: '家禽',
    title: '白羽鸡',
    price: '3030',
    pricepercent: '+22.21%'
  }
]);
</script>
<template>
  <UiTitleCard title="各商品销售情况" class-name="px-0 pb-0 rounded-md overflow-hidden">
    <v-list lines="two" class="py-0" aria-label="page list" aria-busy="true">
      <v-list-item v-for="history in transaction" :key="history.title" :value="history.title" border class="py-5">
        <div class="d-flex align-center justify-space-between w-100 ga-2">
          <div>
            <h6 class="text-subtitle-1 mb-0">{{ history.title }}</h6>
            <span class="text-h6 text-lightText">{{ history.subtitle }}</span>
          </div>
          <div class="text-right">
            <h5 class="text-h5 mb-0 text-primary">{{ history.price }}</h5>
            <span class="text-caption text-lightText">{{ history.pricepercent }}</span>
          </div>
        </div>
      </v-list-item>
    </v-list>
  </UiTitleCard>
</template>
