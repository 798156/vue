<script setup lang="ts">
import { onMounted } from 'vue';
import { useEcomStore } from '@/stores/apps/eCommerce';

const store = useEcomStore();
onMounted(() => {
  store.getsubTotal();
  store.getTotal();
  store.getDiscount();
});
</script>
<template>
  <v-card variant="outlined" class="my-6 bg-surface">
    <h6 class="text-subtitle-1 pa-4 mb-0">订单摘要</h6>
    <v-divider></v-divider>
    <v-table density="compact">
      <tbody>
        <tr>
          <td class="text-h6 text-lightText">商品原价</td>
          <td class="text-right text-subtitle-1">￥{{ store.subTotal }}</td>
        </tr>
        <tr>
          <td class="text-h6 text-lightText">折扣 5%</td>
          <td class="text-right text-subtitle-1">- ￥{{ store.discount }}</td>
        </tr>
        <tr>
          <td class="text-h6 text-lightText">运费</td>
          <td class="text-right text-subtitle-1">- ￥0</td>
        </tr>
      </tbody>
    </v-table>
  </v-card>
  <v-card variant="outlined">
    <v-table>
      <tbody>
        <tr>
          <td class="text-subtitle-1">总计</td>
          <td class="text-right text-subtitle-1">￥{{ store.total }}</td>
        </tr>
      </tbody>
    </v-table>
  </v-card>
</template>
