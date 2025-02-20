<script setup lang="ts">
// assets
import imageEmpty from '@/assets/images/e-commerce/empty.png';

// icons
import { RightOutlined } from '@ant-design/icons-vue';
</script>

<template>
  <v-card variant="outlined" class="bg-surface">
    <v-card-text>
      <v-row class="justify-center align-center text-lg-left text-center pt-16 pb-6">
        <v-col lg="6" md="8" cols="8">
          <v-img :src="imageEmpty" alt="cover" width="80%" class="ml-md-16" />
        </v-col>
        <v-col lg="6" md="8" cols="12">
          <h1 class="text-lg-h1 text-h3 mb-1">将商品添加到您的购物车</h1>
          <p class="text-h5 text-lightText">感谢您的惠顾，希望我们的商品让您满意</p>
          <v-btn class="mt-3" to="/ecommerce/products" variant="flat" size="large" color="primary">
            探索您的商品
            <template v-slot:append>
              <RightOutlined />
            </template>
          </v-btn>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>
