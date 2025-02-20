<script setup lang="ts">
import { ref } from 'vue';

// import BaseBreadcrumb from '@/components/shared/BaseBreadcrumb.vue';

// icons
import { DownloadOutlined } from '@ant-design/icons-vue';

// const page = ref({ title: 'Add New product' });
// const breadcrumbs = ref([
//   {
//     title: 'Ecommerce',
//     disabled: false,
//     href: '#'
//   },
//   {
//     title: 'Add New product',
//     disabled: true,
//     href: '#'
//   }
// ]);

const items = ref(['100', '200', '300', '400']);
const items1 = ref(['1', '2', '3']);
const items2 = ref(['有货', '售罄']);
</script>

<template>
  <!-- <BaseBreadcrumb :title="page.title" :breadcrumbs="breadcrumbs"></BaseBreadcrumb> -->
  <v-row>
    <v-col>
      <v-card variant="outlined" class="bg-surface">
        <v-card-text>
          <v-row>
            <v-col md="6" cols="12">
              <v-card variant="outlined">
                <v-card-text>
                  <div>
                    <v-label class="mb-2">商品名称</v-label>
                    <v-text-field single-line variant="outlined" placeholder="填入商品名称"></v-text-field>
                  </div>
                  <div>
                    <v-label class="mb-2">商品信息</v-label>
                    <v-textarea single-line variant="outlined" rows="3" placeholder="填入商品具体描述"></v-textarea>
                  </div>
                  <div>
                    <v-label class="mb-2">类别</v-label>
                    <v-text-field single-line variant="outlined" rows="3" placeholder="填入商品类别"></v-text-field>
                  </div>
                  <div>
                    <v-label class="mb-2">库存</v-label>
                    <v-autocomplete
                      model-value="200"
                      :items="items"
                      aria-label="autocomplete"
                      color="primary"
                      variant="outlined"
                      hide-details
                      density="default"
                    >
                      <template v-slot:prepend-inner> ⭐ </template>
                    </v-autocomplete>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
            <v-col md="6" cols="12">
              <v-card variant="outlined">
                <v-card-text>
                  <div class="mb-5">
                    <v-label class="mb-2">数量</v-label>
                    <v-autocomplete
                      model-value="1"
                      aria-label="autocomplete"
                      :items="items1"
                      color="primary"
                      variant="outlined"
                      hide-details
                      density="default"
                    >
                    </v-autocomplete>
                  </div>
                  <div class="mb-5">
                    <v-label class="mb-2">库存情况</v-label>
                    <v-autocomplete
                      aria-label="autocomplete"
                      model-value="售罄"
                      :items="items2"
                      color="primary"
                      variant="outlined"
                      hide-details
                      density="default"
                    >
                    </v-autocomplete>
                  </div>
                  <p class="text-h6 text-lightText mb-2">
                    <span class="text-error">* </span>建议分辨率为 640*640 和文件大小
                  </p>
                  <v-btn variant="outlined" color="secondary">
                    <template v-slot:prepend>
                      <DownloadOutlined />
                    </template>
                    点击上传
                  </v-btn>
                  <div class="d-flex justify-end ga-4 mt-16 pt-8">
                    <v-btn variant="outlined" color="secondary" to="/ecommerce/productlist"> 取消</v-btn>
                    <v-btn variant="flat" color="primary"> 添加新商品 </v-btn>
                  </div>
                </v-card-text>
              </v-card>
            </v-col>
          </v-row>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>
