<script setup>
import { ref, shallowRef, onMounted, computed } from 'vue';
import ProductItemVue from './ProductItem.vue';
import { useEcomStore } from '@/stores/apps/eCommerce';
import { orderBy } from 'lodash';
import { useDisplay } from 'vuetify';
import ProductEmplty from './ProductEmplty.vue';
import ProductFilters from './ProductFilters.vue';
import FloatingCart from '../cart/FloatingCart.vue';

// icons
import { SearchOutlined, FilterOutlined } from '@ant-design/icons-vue';

const store = useEcomStore();

onMounted(() => {
  store.fetchProducts();
});

const getProducts = computed(() => {
  return store.products;
});

const sortbyname = shallowRef(['价格  :  高到低', '价格  :  低到高', '   品质   ', ' 新鲜程度 ']);
const selected = ref('价格  :  低到高 ');
const searchValue = ref('');
const sDrawer = ref(false);

const getVisibleProduct = (products, sortBy, search, gender, category) => {
  // SORT BY
  if (sortBy === '   品质   ') {
    products = orderBy(products, ['rating'], ['desc']);
  }
  if (sortBy === '价格  :  高到低') {
    products = orderBy(products, ['salePrice'], ['desc']);
  }
  if (sortBy === '价格  :  低到高') {
    products = orderBy(products, ['salePrice'], ['asc']);
  }
  if (sortBy === ' 新鲜程度 ') {
    products = orderBy(products, ['created'], ['asc']);
  }
  if (gender) {
    products = products.filter((product) => {
      return product.gender.includes(gender);
    });
  }
  if (category !== 'all') {
    products = products.filter((product) => {
      return product.categories.includes(category);
    });
  }
  if (search) {
    products = products.filter((product) => {
      return product.name.toLowerCase().includes(search.value.toLowerCase());
    });
  }

  return products;
};

const filteredProducts = computed(() => {
  return getVisibleProduct(getProducts.value, selected.value, searchValue, store.gender, store.category);
});
const toggleSide = ref(false);
const { lgAndUp } = useDisplay();
const handleToggle = () => {
  toggleSide.value = !toggleSide.value;
};
const handleMobileDrawer = () => {
  sDrawer.value = !sDrawer.value;
};

function AddCart(p) {
  store.AddToCart(p);
}
</script>

<template>
  <v-row>
    <v-col v-if="!toggleSide && lgAndUp" class="filterSidebar">
      <v-card variant="outlined" class="bg-surface">
        <v-card-item class="py-3">
          <v-card-title class="text-subtitle-1">筛选</v-card-title>
        </v-card-item>
        <v-divider></v-divider>
        <v-card-text class="pa-5"> <ProductFilters /> </v-card-text>
      </v-card>
    </v-col>
    <v-col cols>
      <v-card variant="outlined" class="bg-surface mb-6">
        <v-card-item>
          <div class="d-flex ga-2 align-center">
            <v-btn variant="text" color="dark" @Click="!lgAndUp ? handleMobileDrawer() : handleToggle()">
              <FilterOutlined class="mr-1 text-secondary" /> 筛选 </v-btn
            >
            <v-text-field
              variant="outlined"
              v-model="searchValue"
              persistent-placeholder
              placeholder="搜索"
              hide-details
              color="primary"
              style="max-width: 250px"
            >
              <template v-slot:prepend-inner>
                <SearchOutlined class="text-lightText" :style="{ fontSize: '14px' }" />
              </template>
            </v-text-field>
            <div v-if="lgAndUp" class="ml-auto">
              <v-select
                :items="sortbyname"
                role="link"
                color="primary"
                variant="outlined"
                hide-details
                density="compact"
                v-model="selected"
              ></v-select>
            </div>
          </div>
        </v-card-item>
      </v-card>
      <v-row v-if="filteredProducts.length >= 1">
        <v-col :lg="toggleSide ? '3' : '4'" md="3" v-for="product in filteredProducts" :key="product.id">
          <ProductItemVue
            :name="product.name"
            :image="product.image"
            :desc="product.description"
            :salePrice="product.salePrice"
            :offerPrice="product.offerPrice"
            :rating="product.rating"
            :goto="product.id"
            @handlecart="AddCart(product)"
          />
        </v-col>
      </v-row>
      <ProductEmplty v-else />
    </v-col>
  </v-row>
  <v-navigation-drawer temporary location="left" v-model="sDrawer" width="300" top v-if="!lgAndUp">
    <v-card-text class="pa-5">
      <ProductFilters />
    </v-card-text>
  </v-navigation-drawer>
  <FloatingCart />
</template>
<style lang="scss">
.filterSidebar {
  max-width: 350px;
}
</style>
