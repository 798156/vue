<script setup lang="ts">
import { ref, shallowRef } from 'vue';
import ColorsOptions from './colorsOption';
import { useEcomStore } from '@/stores/apps/eCommerce';

const range = shallowRef([0, 300]);

const store = useEcomStore();

const selectedGender = ref('');
store.SelectGender(selectedGender);

const selectedCategory = ref('all');
store.SelectCategory(selectedCategory);

const selectRating = ref(0);
const setColor = ref(1);
function selectColor(e: number) {
  setColor.value = e;
}
</script>
<template>
  <v-list lines="one" aria-label="gender list" aria-busy="true">
    <v-list-item-title class="text-h5">分类</v-list-item-title>
    <v-list-item class="pa-0 ml-n2 mb-n2">
      <v-checkbox label="农副产品" v-model="selectedGender" color="primary" value="农副产品" hide-details> </v-checkbox>
    </v-list-item>
    <v-list-item class="pa-0 ml-n2 mb-n2">
      <v-checkbox label="蔬菜" v-model="selectedGender" color="secondary" value="蔬菜" hide-details></v-checkbox>
    </v-list-item>
    <v-list-item class="pa-0 ml-n2 mb-n2">
      <v-checkbox label="禽类" v-model="selectedGender" color="secondary" value="禽类" hide-details></v-checkbox>
    </v-list-item>
    <v-list-item class="pa-0 ml-n2">
      <v-checkbox label="水果" v-model="selectedGender" color="error" value="水果" hide-details></v-checkbox>
    </v-list-item>
   
  </v-list>
  <v-list lines="one" class="mb-3" aria-label="categories list" aria-busy="true">
    <v-list-item-title class="text-h5">产地</v-list-item-title>
    <v-list-item class="pa-0 ml-n2 mb-n2">
      <v-checkbox label="所有" v-model="selectedCategory" color="primary" value="all" hide-details> </v-checkbox>
    </v-list-item>
    <v-list-item class="pa-0 ml-n2 mb-n2">
      <v-checkbox label="浙江" v-model="selectedCategory" color="primary" value="浙江" hide-details></v-checkbox>
    </v-list-item>
    <v-list-item class="pa-0 ml-n2 mb-n2">
      <v-checkbox label="云南" v-model="selectedCategory" color="primary" value="云南" hide-details></v-checkbox>
    </v-list-item>
    <v-list-item class="pa-0 ml-n2 mb-n2">
      <v-checkbox label="广西" v-model="selectedCategory" color="primary" value="广西" hide-details></v-checkbox>
    </v-list-item>
    <v-list-item class="pa-0 ml-n2 mb-n2">
      <v-checkbox label="新疆" v-model="selectedCategory" color="primary" value="新疆" hide-details></v-checkbox>
    </v-list-item>
    <v-list-item class="pa-0 ml-n2 mb-n2">
      <v-checkbox label="海南" v-model="selectedCategory" color="primary" value="海南" hide-details></v-checkbox>
    </v-list-item>
  </v-list>
  <!-- <div class="mb-3">
    <h5 class="text-h5 mb-0">颜色</h5>
    <div class="d-flex ga-2 flex-wrap v-col-11 px-0">
      <template v-for="(catcolor, i) in ColorsOptions" :key="i">
        <v-avatar class="cursor-pointer" :color="catcolor.value" variant="flat" size="small" @click="selectColor(i)">
          <template v-if="setColor == i">
            <CheckIcon size="13" />
          </template>
        </v-avatar>
      </template>
    </div>
  </div> -->
  <v-divider :thickness="13" color="success"></v-divider>
  <div class="mb-3">
    <v-col class="pa-0 text-center">  &nbsp; </v-col>
    <h5 class="text-h5">价格</h5>
    <v-row>
      <v-col cols="6">
        <v-label class="mb-2 text-lightText">最小</v-label>
        <v-text-field v-model="range[0]" aria-label="min" hide-details single-line type="number" variant="outlined"></v-text-field>
      </v-col>
      <v-col cols="6">
        <v-label class="mb-2 text-lightText">最大</v-label>
        <v-text-field v-model="range[1]" aria-label="max" hide-details single-line type="number" variant="outlined"></v-text-field>
      </v-col>
    </v-row>
    <div aria-label="Select a value within the range of 0 to 1000">
      <v-range-slider
        v-model="range"
        color="primary"
        thumb-size="16"
        track-color="secondary200"
        track-size="4"
        tick-size="4"
        :max="1000"
        :min="0"
        :step="1"
        hide-details
        class="mt-2"
      ></v-range-slider>
    </div>
  </div>
  <div>
    <h5 class="text-h5 mb-0">口碑</h5>
    <div class="d-flex align-center">
      <v-rating
        hover
        half-increments
        v-model="selectRating"
        class="ma-2"
        density="compact"
        color="inputBorder"
        active-color="warning"
      ></v-rating>
      <pre class="mb-0 text-h6">({{ selectRating }})</pre>
    </div>
  </div>
  <v-btn color="primary" variant="text" block class="mt-5">重置所有筛选条件</v-btn>
</template>
<style lang="scss">
.custom-accordion {
  padding: 18px 2px;

  min-height: 30px !important;
  .v-expansion-panel-title__overlay {
    background-color: transparent;
  }
}
.acco-body {
  .v-expansion-panel-text__wrapper {
    padding: 5px 0;
  }
}
.custom-radio-box {
  .v-selection-control-group {
    flex-direction: row;
    flex-wrap: wrap;
  }
  .v-selection-control {
    flex: 50%;
  }
}
</style>
