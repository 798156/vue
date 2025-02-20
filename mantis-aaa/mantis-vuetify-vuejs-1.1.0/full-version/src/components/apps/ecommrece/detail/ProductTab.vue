<script setup lang="ts">
import { ref } from 'vue';
import ProductDescription from './ProductDescription.vue';
import ProductReview from './ProductReview.vue';
import ProductSpecification from './ProductSpecification.vue';

const tab = ref(null);
</script>

<template>
  <v-tabs v-model="tab" color="primary" class="border-bottom">
    <v-tab value="one">商品特征</v-tab>
    <v-tab value="two">商品规格</v-tab>
    <v-tab value="three">商品概述</v-tab>
    <v-tab value="four">买家评论 <v-chip color="secondary" size="small" class="ml-1">275</v-chip></v-tab>
  </v-tabs>
  <div class="mt-5">
    <v-window v-model="tab">
      <v-window-item value="one">
        <ProductDescription />
      </v-window-item>
      <v-window-item value="two">
        <ProductSpecification />
      </v-window-item>
      <v-window-item value="three">
        <p class="text-h6 text-lightText">
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;台州涌泉蜜橘，产自浙江台州的特色柑橘品种，以其皮薄多汁、甜度高而闻名。涌泉镇位于台州市椒江区，这里山清水秀，土壤肥沃，空气清新，为蜜橘的生长提供了得天独厚的自然条件。涌泉蜜橘的种植历史悠久，
          早在明代就有记载，至今已有400多年的历史。涌泉蜜橘的种植面积达到了10000多亩，年产量达到了5000多吨，是台州市的特色农产品之一。
        </p>
        <p class="text-h6 text-lightText mb-0">
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;每年秋季成熟，是馈赠亲友的上佳礼品，果实色泽鲜艳，肉质细腻，入口即化，被誉为“桔中之王”。
          深受消费者喜爱。其独特的地理环境和气候条件，使得台州涌泉蜜橘品质上乘，畅销国内外市场。
        </p>
      </v-window-item>
      <v-window-item value="four">
        <ProductReview />
      </v-window-item>
    </v-window>
  </div>
</template>
