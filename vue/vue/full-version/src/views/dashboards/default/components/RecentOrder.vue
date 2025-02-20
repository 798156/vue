<script setup lang="ts">
import { shallowRef } from 'vue';

import UiTitleCard from '@/components/shared/UiTitleCard.vue';

const projects = shallowRef([
  {
    number: 13256498,
    order: 125,
    name: '绍兴无沙梅干菜',
    amount: '￥709',
    priority: 'pending'
  },
  {
    number: 13286564,
    order: 100,
    name: '人参果 | 西兰花',
    amount: '￥8338',
    priority: 'approved'
  },
  {
    number: 84564564,
    order: 40,
    name: '土鸡蛋 | 哈密瓜 | 白羽鸡',
    amount: '￥4050',
    priority: 'rejected'
  },
  {
    number: 86739658,
    order: 50,
    name: '涌泉蜜桔 | 圣女果',
    amount: '￥4107',
    priority: 'pending'
  },
  {
    number: 98652366,
    order: 16,
    name: '木瓜 | 西瓜',
    amount: '￥239',
    priority: 'approved'
  },
  {
    number: 98753263,
    order: 89,
    name: '土鸡蛋',
    amount: '￥105',
    priority: 'rejected'
  },
  {
    number: 98753275,
    order: 85,
    name: '圣女果 | 西兰花',
    amount: '￥980',
    priority: 'approved'
  },
  {
    number: 98753291,
    order: 60,
    name: '白羽鸡 | 土鸡蛋',
    amount: '￥1401',
    priority: 'pending'
  },
  {
    number: 98756325,
    order: 11,
    name: '哈密瓜 | 木瓜 | 涌泉蜜桔 | 圣女果',
    amount: '￥989',
    priority: 'approved'
  },
  {
    number: 98764564,
    order: 41,
    name: '绍兴无沙梅干菜 | 涌泉蜜桔',
    amount: '￥139',
    priority: 'pending'
  }
]);
</script>

<template>
  <UiTitleCard title="最近的订单" class-name="px-0 pb-0 rounded-md">
    <v-table class="bordered-table" hover density="comfortable">
      <thead class="bg-containerBg">
        <tr>
          <th class="text-left text-caption font-weight-bold text-uppercase">订单号</th>
          <th class="text-left text-caption font-weight-bold text-uppercase">商品名称</th>
          <th class="text-right text-caption font-weight-bold text-uppercase" style="min-width: 100px">订单数量</th>
          <th class="text-left text-caption font-weight-bold text-uppercase">快递情况</th>
          <th class="text-right text-caption font-weight-bold text-uppercase">订单总价</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in projects" :key="item.name">
          <td class="py-3">
            <router-link to="/dashboard/default" class="text-secondary link-hover">{{ item.number }}</router-link>
          </td>
          <td class="py-3">{{ item.name }}</td>
          <td class="py-3 text-right" style="min-width: 100px">{{ item.order }}</td>
          <td class="py-3">
            <v-chip variant="text" size="small" class="px-0" v-if="item.priority === 'rejected'">
              <v-avatar size="8" color="error" variant="flat" class="mr-2"></v-avatar>
              <p class="text-h6 mb-0">拒绝</p>
            </v-chip>
            <v-chip variant="text" size="small" class="px-0" v-else-if="item.priority === 'approved'">
              <v-avatar size="8" color="success" variant="flat" class="mr-2"></v-avatar>
              <p class="text-h6 mb-0">已签收</p>
            </v-chip>
            <v-chip variant="text" size="small" class="px-0" v-else>
              <v-avatar size="8" color="warning" variant="flat" class="mr-2"></v-avatar>
              <p class="text-h6 mb-0">处理中……</p>
            </v-chip>
          </td>
          <td class="py-3 text-right" style="min-width: 100px">{{ item.amount }}</td>
        </tr>
      </tbody>
    </v-table>
  </UiTitleCard>
</template>
