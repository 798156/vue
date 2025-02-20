<script setup lang="ts">
import { onMounted, ref } from 'vue';
import AddressCard from './AddressCard.vue';
import { useEcomStore } from '@/stores/apps/eCommerce';

// icons
import { AppstoreOutlined } from '@ant-design/icons-vue';

const store = useEcomStore();
onMounted(() => {
  store.fetchAddress();
});
const ls = [
  {
    name: '朱钱宁',
    destination: '家',
    isDefault: true,
    building: '24号大街',
    street: '755号',
    city: '保利玫瑰之湾',
    state: '浙江',
    country: '杭州',
    post: '钱塘',
    phone: '19875481124'
  },
  {
    name: '朱钱宁',
    destination: '公司',
    isDefault: false,
    building: '滨江区 ',
    street: '华为技术有限公司研究所 ',
    city: '56M3+M9',
    state: '浙江',
    country: '杭州',
    post: '江虹路',
    phone: '081-85435721'
  }
]


const selected = ref(['shipping']);
</script>

<template>
  <v-card variant="outlined" class="bg-surface">
    <v-card-text class="pa-0">
      <h4 class="text-subtitle-1 pa-4">快递信息</h4>
      <v-divider></v-divider>
    </v-card-text>
    <v-card-text>
      <v-row>
        <v-col sm="6" cols="12" v-for="address in ls" :key="address.id">
          <AddressCard
            :name="address.name"
            :destination="address.destination"
            :isDefault="address.isDefault"
            :building="address.building"
            :street="address.street"
            :city="address.city"
            :state="address.state"
            :country="address.country"
            :post="address.post"
            :phone="address.phone"
            :showBtn="true"
          />
        </v-col>
        <v-col lg="12">
          <v-row class="align-center mb-sm-n3 mb-n1">
            <v-col cols="12" sm="3" class="pb-sm-3 pb-1">
              <v-label>姓氏 :</v-label>
            </v-col>
            <v-col cols="12" sm="9" class="pt-sm-3 pt-0">
              <v-text-field hide-details color="primary" placeholder="填入你的姓氏" variant="outlined"></v-text-field>
            </v-col>
          </v-row>
          <v-row class="align-center mb-sm-n3 mb-n1">
            <v-col cols="12" sm="3" class="pb-sm-3 pb-1">
              <v-label>名  :</v-label>
            </v-col>
            <v-col cols="12" sm="9" class="pt-sm-3 pt-0">
              <v-text-field hide-details color="primary" placeholder="填入你的名字" variant="outlined"></v-text-field>
            </v-col>
          </v-row>
          <v-row class="align-center mb-sm-n3 mb-n1">
            <v-col cols="12" sm="3" class="pb-sm-3 pb-1">
              <v-label>邮箱 :</v-label>
            </v-col>
            <v-col cols="12" sm="9" class="pt-sm-3 pt-0">
              <v-text-field hide-details color="primary" type="email" placeholder="填入你的邮箱" variant="outlined"></v-text-field>
            </v-col>
          </v-row>
          <v-row class="align-center mb-sm-n3 mb-n1">
            <v-col cols="12" sm="3" class="pb-sm-3 pb-1">
              <v-label>生日 :</v-label>
            </v-col>
            <v-col cols="12" sm="9" class="pt-sm-3 pt-0">
              <v-row class="align-center">
                <v-col cols="3" class="pr-0">
                  <v-text-field hide-details color="primary" type="number" placeholder="21" variant="outlined">
                    <template v-slot:append-inner>
                      <AppstoreOutlined class="text-lightText" />
                    </template>
                  </v-text-field>
                </v-col>
                <v-col class="pa-0 text-center"> / </v-col>
                <v-col cols="3" class="px-0">
                  <v-text-field hide-details color="primary" type="number" placeholder="12" variant="outlined">
                    <template v-slot:append-inner>
                      <AppstoreOutlined class="text-lightText" />
                    </template>
                  </v-text-field>
                </v-col>
                <v-col class="pa-0 text-center"> / </v-col>
                <v-col cols="4" class="pl-0">
                  <v-text-field hide-details color="primary" type="number" placeholder="2025" variant="outlined">
                    <template v-slot:append-inner>
                      <AppstoreOutlined class="text-lightText" />
                    </template>
                  </v-text-field>
                </v-col>
              </v-row>
            </v-col>
          </v-row>
          <v-row class="align-center mb-sm-n3 mb-n1">
            <v-col cols="12" sm="3" class="pb-sm-3 pb-1">
              <v-label>电话号码 :</v-label>
            </v-col>
            <v-col cols="12" sm="9" class="pt-sm-3 pt-0">
              <v-row>
                <v-col cols="3" sm="2" class="pr-0">
                  <v-text-field hide-details color="primary" type="number" placeholder="+86" variant="outlined"></v-text-field>
                </v-col>
                <v-col cols="9" sm="10">
                  <v-text-field hide-details color="primary" type="number" placeholder="19857……" variant="outlined">
                    <template v-slot:append-inner>
                      <AppstoreOutlined class="text-lightText" />
                    </template>
                  </v-text-field>
                </v-col>
              </v-row>
            </v-col>
          </v-row>
          <v-row class="align-center mb-sm-n3 mb-n1">
            <v-col cols="12" sm="3" class="pb-sm-3 pb-1">
              <v-label>地址 :</v-label>
            </v-col>
            <v-col cols="12" sm="9" class="pt-sm-3 pt-0">
              <v-text-field hide-details color="primary" placeholder="填入你的地址" variant="outlined"></v-text-field>
            </v-col>
          </v-row>
          <v-checkbox
            class="mt-3"
            v-model="selected"
            label="保存此新地址以备将来发货"
            color="primary"
            value="shipping"
            hide-details
          ></v-checkbox>
          <v-row class="mt-2">
            <v-col cols="12" class="text-right">
              <v-btn color="secondary" class="mr-2" variant="outlined">取消</v-btn>
              <v-btn color="primary" variant="flat">暂存</v-btn>
            </v-col>
          </v-row>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>
