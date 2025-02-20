<script setup lang="ts">
import { shallowRef } from 'vue';

type GenealType = {
  title: string;
  desc: string;
};

type SpecificationType = {
  title: string;
  desc: string;
};

const generalItem = shallowRef<GenealType[]>([
  {
    title: '商品分类:',
    desc: '水果'
  },
  {
    title: '商品编号:',
    desc: '103346615694'
  },
  {
    title: '产地 :',
    desc: '台州'
  }
]);

const specificationItem = shallowRef<SpecificationType[]>([
  {
    title: '商家名称 :',
    desc: '称心如意'
  },
  {
    title: '口碑:',
    desc: '4.5⭐'
  },
  {
    title: '联系方式:',
    desc: '+86 137508222419'
  }
]);
</script>
<template>
  <v-row>
    <v-col cols="12" sm="6">
      <h5 class="text-h5 mb-4">商品分类</h5>
      <v-divider></v-divider>
      <v-table class="mt-4">
        <tr v-for="(gen, i) in generalItem" :key="i">
          <td class="py-2">
            <span class="text-h6 text-lightText">{{ gen.title }}</span>
          </td>
          <td>{{ gen.desc }}</td>
        </tr>
      </v-table>
    </v-col>
    <v-col cols="12" sm="6">
      <h5 class="text-h5 mb-4">商家详细信息</h5>
      <v-divider></v-divider>
      <v-table class="mt-4">
        <tr v-for="(item, i) in specificationItem" :key="i">
          <td class="py-2">
            <span class="text-h6 text-lightText">{{ item.title }}</span>
          </td>
          <td>{{ item.desc }}</td>
        </tr>
      </v-table>
    </v-col>
  </v-row>
</template>
