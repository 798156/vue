<script setup lang="ts">
import { ref } from 'vue';

const progressData = ref([
  {
    title: '已发布商品',
    color: 'primary',
    value: 30
  },
  {
    title: '已完成的销售额',
    color: 'success',
    value: 90
  },
  {
    title: '在处理的订单',
    color: 'error',
    value: 50
  },
  {
    title: '期望预算',
    color: 'warning',
    value: 55
  }
]);
</script>

<template>
  <v-card elevation="0" variant="outlined" class="overflow-hidden bg-surface">
    <v-card-text>
      <v-row v-for="progress in progressData" :key="progress.color">
        <v-col cols="6">
          <p class="text-h6 mb-0">{{ progress.title }}</p>
        </v-col>
        <v-col cols="6">
          <div class="d-flex align-center">
            <v-progress-linear
              aria-label="progressbar"
              :color="progress.color"
              :model-value="progress.value"
              height="6"
              rounded
            ></v-progress-linear>
            <span class="text-caption text-lightText ml-8 d-block">{{ progress.value }}%</span>
          </div>
        </v-col>
      </v-row>
      <v-divider class="mt-2"></v-divider>
      <v-list class="py-0 mt-5" aria-label="budget" aria-busy="true">
        <v-list-item class="pa-0">
          <template v-slot:prepend>
            <v-avatar size="40" variant="flat">
              <img src="@/assets/images/analytics/target.svg" width="40" alt="icon" />
            </v-avatar>
          </template>
          <v-list-item-title class="text-h6">收入⭐薪金⭐预算</v-list-item-title>
          <p class="text-caption text-lightText mb-0">您所有的收入、薪金和预算都在这里，您可以跟踪或管理它们</p>
        </v-list-item>
      </v-list>
    </v-card-text>
  </v-card>
</template>
