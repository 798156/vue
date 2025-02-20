<script setup lang="ts">
import { shallowRef } from 'vue';

type GenealType = {
  title: string;
  desc: string;
};

const generalItem = shallowRef<GenealType[]>([
  {
    title: '品种 :',
    desc: '蜜桔'
  },
  {
    title: '特产品类 :',
    desc: '涌泉蜜桔'
  },
  {
    title: '原产地 :',
    desc: '浙江'
  },
  {
    title: '国产|进口 :',
    desc: '国产'
  },
  {
    title: '贮存条件 :',
    desc: '冷藏 | 常温'
  },
  {
    title: '配送时间 :',
    desc: '承诺2-3天内发货'
  }
]);
</script>
<template>
  <v-table>
    <tr v-for="(gen, i) in generalItem" :key="i">
      <td class="py-2">
        <span class="text-h6 text-lightText">{{ gen.title }}</span>
      </td>
      <td>{{ gen.desc }}</td>
    </tr>
  </v-table>
</template>
