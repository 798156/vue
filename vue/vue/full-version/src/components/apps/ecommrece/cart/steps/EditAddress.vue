<script setup lang="ts">
import { ref } from 'vue';

// icons
import { EditOutlined, CloseCircleOutlined } from '@ant-design/icons-vue';

const props = defineProps({
  name: String,
  destination: String,
  building: String,
  street: String,
  city: String,
  state: String,
  country: String,
  post: String,
  phone: String,
  isDefault: Boolean,
  showBtn: Boolean
});

const dialog = ref(false);

const radioGroup = ref('1');
</script>
<template>
  <v-card variant="outlined">
    <v-card-text>
      <div class="d-flex align-center ga-2">
        <h6 class="text-subtitle-1 mb-0">{{ props.name }}</h6>
        <small class="text-lightText text-caption">({{ props.destination }})</small>
        <div class="ml-auto">
          <v-dialog v-model="dialog" width="800">
            <template v-slot:activator="{ props }">
              <v-btn color="secondary" size="small" variant="outlined" v-bind="props">
                <template v-slot:prepend>
                  <EditOutlined />
                </template>
                更改
              </v-btn>
            </template>
            <v-card>
              <v-card-title class="py-4 d-flex justify-space-between align-center">
                <span class="text-subtitle-1">联系人收货地址</span>
                <v-btn icon rounded class="ml-auto" variant="text" @click="dialog = false">
                  <CloseCircleOutlined class="text-primary" :style="{ fontSize: '13px' }" />
                </v-btn>
              </v-card-title>
              <v-divider></v-divider>
              <v-card-text class="px-2">
                <v-container>
                  <v-row>
                    <v-col cols="12" sm="6">
                      <v-label class="mb-2">姓名</v-label>
                      <v-text-field
                        single-line
                        variant="outlined"
                        color="primary"
                        model-value="朱钱宁"
                        required
                        hide-details
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-label class="mb-2">标签</v-label>
                      <v-radio-group inline hide-details v-model="radioGroup">
                        <v-radio color="primary" value="1" label="家"></v-radio>
                        <v-radio color="primary" value="2" label="公司"></v-radio>
                      </v-radio-group>
                    </v-col>
                    <v-col cols="12">
                      <v-label class="mb-2">省份</v-label>
                      <v-text-field
                        single-line
                        variant="outlined"
                        color="primary"
                        model-value="浙江省"
                        required
                        hide-details
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12">
                      <v-label class="mb-2">街道</v-label>
                      <v-text-field
                        single-line
                        variant="outlined"
                        color="primary"
                        model-value="白杨街道"
                        required
                        hide-details
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-label class="mb-2">城市</v-label>
                      <v-text-field
                        single-line
                        variant="outlined"
                        color="primary"
                        model-value="杭州"
                        required
                        hide-details
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-label class="mb-2">详细地址</v-label>
                      <v-text-field single-line variant="outlined" color="primary" model-value="滨江" required hide-details></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-label class="mb-2">国家</v-label>
                      <v-text-field
                        single-line
                        variant="outlined"
                        color="primary"
                        model-value="中国"
                        required
                        hide-details
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-label class="mb-2">邮编</v-label>
                      <v-text-field
                        single-line
                        variant="outlined"
                        color="primary"
                        model-value="310000"
                        required
                        hide-details
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12">
                      <v-label class="mb-2">联系方式</v-label>
                      <v-text-field
                        single-line
                        variant="outlined"
                        color="primary"
                        model-value="+86 13750822418"
                        required
                        hide-details
                      ></v-text-field>
                    </v-col>
                    <v-col cols="12">
                      <v-switch color="primary" :model-value="true" label="默认" hide-details></v-switch>
                    </v-col>
                  </v-row>
                </v-container>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="error" variant="text" @click="dialog = false">取消 </v-btn>
                <v-btn color="primary" variant="flat" @click="dialog = false"> 递交 </v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
        </div>
      </div>
      <div class="mt-2 text-body1">
        <p class="text-caption text-lightText">
          {{ props.building }}, {{ props.street }}, {{ props.city }}, {{ props.state }}, {{ props.country }} - {{ props.post }}
        </p>
        <p class="text-caption text-lightText mb-0">{{ props.phone }}</p>
      </div>
    </v-card-text>
  </v-card>
</template>
