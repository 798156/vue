<script setup lang="ts">
import { shallowRef } from 'vue';

// icons
import { RiseOutlined, FallOutlined } from '@ant-design/icons-vue';

const fivecards = shallowRef([
  {
    name: '页面总浏览量',
    earn: '4,42,61',
    percent: '59.3%',
    color: 'primary',
    icon: RiseOutlined,
    text: '105,30浏览量'
  },
  {
    name: '注册用户总量',
    earn: '78,250',
    percent: '10.5%',
    color: 'error',
    icon: FallOutlined,
    text: '8,90新用户'
  },
  {
    name: '订单总量',
    earn: '18,800',
    percent: '27.4%',
    color: 'warning',
    icon: RiseOutlined,
    text: '190新的订单'
  },
  {
    name: '商品总营收',
    earn: '￥35,078',
    percent: '27.4%',
    color: 'success',
    icon: RiseOutlined,
    text: '￥2039'
  }
]);
</script>
<template>
  <v-row class="my-0">
    <v-col cols="12" sm="6" md="3" v-for="(card5, i) in fivecards" :key="i" :value="card5">
      <v-card elevation="0">
        <v-card variant="outlined">
          <v-card-text>
            <div class="d-flex align-items-center justify-space-between">
              <div>
                <h6 class="text-h6 text-lightText mb-1">{{ card5.name }}</h6>
                <h4 class="text-h4 d-flex align-center mb-0">
                  {{ card5.earn }}
                  <v-chip :color="card5.color" :border="`${card5.color} solid thin opacity-50`" class="ml-2" size="small" label>
                    <template v-slot:prepend>
                      <component :is="card5.icon" :style="{ fontSize: '12px' }" :class="'mr-1 text-' + card5.color" />
                    </template>
                    {{ card5.percent }}
                  </v-chip>
                </h4>
                <span class="text-lightText text-caption pt-5 d-block"
                  >您获得了<span :class="'text-' + card5.color">{{ card5.text }}</span> 在今天</span
                >
              </div>
            </div>
          </v-card-text>
        </v-card>
      </v-card>
    </v-col>
  </v-row>
</template>
