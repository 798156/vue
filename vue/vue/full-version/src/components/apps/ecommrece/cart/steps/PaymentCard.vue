<script setup lang="ts">
import { ref } from 'vue';
import { useEcomStore } from '@/stores/apps/eCommerce';
import EditAddress from './EditAddress.vue';

// icons
import { CheckOutlined } from '@ant-design/icons-vue';

const payment = ref('credit');

const store = useEcomStore();

const ls = [
  {
    id: 1,
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
]
</script>

<template>
  <v-card variant="outlined" class="bg-surface">
    <v-card-item>
      <h5 class="text-subtitle-1 mb-0">付款方式</h5>
    </v-card-item>
    <v-divider></v-divider>
    <v-card-text>
      <div v-for="address in ls" :key="address.id">
        <div v-if="address.isDefault">
          <EditAddress
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
            :showBtn="false"
          />
        </div>
      </div>
      <v-row class="mt-3">
        <v-col cols="12">
          <v-radio-group v-model="payment" hide-details>
            <v-row>
              <v-col cols="12" lg="auto" sm="6">
                <div class="py-5 px-4 border payment-method rounded-md">
                  <v-radio value="credit" color="primary" class="label-op-1">
                    <template v-slot:label>
                      <div class="d-flex align-center w-100">
                        <div class="flex-1-1">
                          <div class="d-flex justify-space-between">
                            <h6 class="text-subtitle-1 mb-1">银行卡</h6>
                            <div class="ml-auto">
                              <img src="@/assets/images/e-commerce/card.png" width="50" alt="img" />
                            </div>
                          </div>
                          <span class="d-block text-caption text-lightText text-wrap">第一次使用可享受10%折扣</span>
                        </div>
                      </div>
                    </template>
                  </v-radio>
                </div>
              </v-col>
              <v-col cols="12" lg="auto" sm="6">
                <div class="py-5 px-4 border payment-method rounded-md">
                  <v-radio value="paypal" color="primary" class="label-op-1">
                    <template v-slot:label>
                      <div class="d-flex align-start w-100">
                        <div>
                          <h6 class="text-subtitle-1 mb-1">支付宝</h6>
                          <span class="d-block text-caption text-lightText text-wrap">第一次使用可享受5%折扣</span>
                        </div>
                        <div class="ml-auto">
                          <img src="@/assets/images/e-commerce/paypal.png" width="55" alt="img" />
                        </div>
                      </div>
                    </template>
                  </v-radio>
                </div>
              </v-col>
              <v-col cols="12" lg="auto" sm="6">
                <div class="py-5 px-4 border payment-method rounded-md">
                  <v-radio value="cash" color="primary" class="label-op-1">
                    <template v-slot:label>
                      <div class="d-flex align-center w-100">
                        <div>
                          <h6 class="text-subtitle-1 mb-1">——货到付款——</h6>
                          <span class="d-block text-caption text-lightText text-wrap">——当你使用此付款时——</span>
                        </div>
                      </div>
                    </template>
                  </v-radio>
                </div>
              </v-col>
            </v-row>
          </v-radio-group>
        </v-col>
        <v-col cols="12">
          <v-card elevation="0" variant="text" :disabled="payment !== 'credit'" v-if="payment == 'credit'">
            <v-card-item class="py-3 px-0">
              <v-row class="mb-md-n3 mb-n1">
                <v-col md="5" cols="12" class="pb-md-3 pb-1">
                  <v-label>银行卡号 :</v-label>
                  <span class="text-caption text-lightText d-block">输入银行卡号</span>
                </v-col>
                <v-col md="7" cols="12" class="pt-md-3 pt-0">
                  <v-text-field single-line variant="outlined" hide-details>
                    <template v-slot:prepend-inner>
                      <img src="@/assets/images/e-commerce/master-card.png" width="20" alt="img" />
                    </template>
                    <template v-slot:append-inner>
                      <CheckOutlined class="text-lightText" />
                    </template>
                  </v-text-field>
                </v-col>
              </v-row>
              <v-row class="mb-md-n3 mb-n1">
                <v-col md="5" cols="12" class="pb-md-3 pb-1">
                  <v-label>付款时间 :</v-label>
                  <span class="text-caption text-lightText d-block">输入付款时间</span>
                </v-col>
                <v-col md="7" cols="12" class="pt-md-3 pt-0">
                  <v-row class="align-center">
                    <v-col cols="5" class="pr-0">
                      <v-text-field single-line type="number" placeholder="3" variant="outlined" hide-details></v-text-field>
                    </v-col>
                    <v-col cols="2" class="pa-0 text-center"> / </v-col>
                    <v-col cols="5" class="pl-0">
                      <v-text-field single-line type="number" placeholder="2025" variant="outlined" hide-details></v-text-field>
                    </v-col>
                  </v-row>
                </v-col>
              </v-row>
              <v-row class="mb-md-n3 mb-n1">
                <v-col md="5" cols="12" class="pb-md-3 pb-1">
                  <v-label>银行卡密码 :</v-label>
                  <span class="text-caption text-lightText d-block">输入银行卡密码</span>
                </v-col>
                <v-col md="7" cols="12" class="pt-md-3 pt-0">
                  <v-text-field single-line variant="outlined" hide-details>
                    <template v-slot:prepend-inner>
                      <img src="@/assets/images/e-commerce/cvv.png" width="20" alt="img" />
                    </template>
                  </v-text-field>
                </v-col>
              </v-row>
              <v-row class="mb-md-n3 mb-n1">
                <v-col md="5" cols="12" class="pb-md-3 pb-1">
                  <v-label>验证码 :</v-label>
                  <span class="text-caption text-lightText d-block">输入验证码</span>
                </v-col>
                <v-col md="7" cols="12" class="pt-md-3 pt-0">
                  <v-text-field single-line variant="outlined" hide-details>
                    <template v-slot:prepend-inner>
                      <img src="@/assets/images/e-commerce/lock.png" width="20" alt="img" />
                    </template>
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="text-right">
                  <v-btn variant="outlined" class="mr-2" color="secondary">取消</v-btn>
                  <v-btn variant="flat" color="primary">保存</v-btn>
                </v-col>
                <v-col cols="12" class="d-flex align-center">
                  <v-divider />
                  <div class="px-2">***</div>
                  <v-divider />
                </v-col>
              </v-row>
            </v-card-item>
            <v-card-text class="mt-4 px-0 pb-0">
              <v-row>
                <v-col cols="12" sm="6" lg="5">
                  <v-card elevation="0" variant="outlined" class="object-card overflow-hidden">
                    <v-card-text class="top-object">
                      <div class="d-flex mb-12">
                        <div>
                          <h5 class="text-h5 mb-0">江方奇</h5>
                          <h6 class="text-h5">137508272419</h6>
                        </div>
                        <div class="ml-auto">
                          <img src="@/assets/images/e-commerce/mastercard.png" width="42" alt="img" />
                        </div>
                      </div>

                      <div class="d-flex align-center justify-space-between mt-3">
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">支付宝</span>
                          <span class="text-caption d-block"></span>
                        </div>
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">上一次支付时间</span>
                          <span class="text-caption d-block">2/22</span>
                        </div>
                      </div>
                    </v-card-text>
                  </v-card>
                </v-col>
                <v-col cols="12" sm="6" lg="5">
                  <v-card elevation="0" variant="outlined" class="object-card overflow-hidden">
                    <v-card-text class="top-object">
                      <div class="d-flex mb-12">
                        <div>
                          <h5 class="text-h5 mb-0">朱钱宁</h5>
                          <h6 class="text-h5">19875481124</h6>
                        </div>
                        <div class="ml-auto">
                          <img src="@/assets/images/e-commerce/visa.png" width="24" alt="img" />
                        </div>
                      </div>

                      <div class="d-flex align-center justify-space-between mt-3">
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">微信</span>
                          <span class="text-caption d-block"></span>
                        </div>
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">上一次支付时间</span>
                          <span class="text-caption d-block">3/25</span>
                        </div>
                      </div>
                    </v-card-text>
                  </v-card>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
          <v-card elevation="0" variant="text" v-if="payment == 'paypal'">
            <v-card-item class="py-3 px-0">
              <v-row class="mb-md-n3 mb-n1">
                <v-col md="5" cols="12" class="pb-md-3 pb-1">
                  <v-label>卡号 :</v-label>
                  <span class="text-caption text-lightText d-block">输入卡号</span>
                </v-col>
                <v-col md="7" cols="12" class="pt-md-3 pt-0">
                  <v-text-field single-line variant="outlined" hide-details>
                    <template v-slot:prepend-inner>
                      <img src="@/assets/images/e-commerce/paypal.png" width="40" alt="img" />
                    </template>
                    <template v-slot:append-inner>
                      <CheckOutlined class="text-lightText" />
                    </template>
                  </v-text-field>
                </v-col>
              </v-row>
              <v-row class="mb-md-n3 mb-n1">
                <v-col md="5" cols="12" class="pb-md-3 pb-1">
                  <v-label>付款时间 :</v-label>
                  <span class="text-caption text-lightText d-block">输入付款时间</span>
                </v-col>
                <v-col md="7" cols="12" class="pt-md-3 pt-0">
                  <v-row class="align-center">
                    <v-col cols="5" class="pr-0">
                      <v-text-field single-line type="number" placeholder="2" variant="outlined" hide-details></v-text-field>
                    </v-col>
                    <v-col cols="2" class="pa-0 text-center"> / </v-col>
                    <v-col cols="5" class="pl-0">
                      <v-text-field single-line type="number" placeholder="2025" variant="outlined" hide-details></v-text-field>
                    </v-col>
                  </v-row>
                </v-col>
              </v-row>
              <v-row class="mb-md-n3 mb-n1">
                <v-col md="5" cols="12" class="pb-md-3 pb-1">
                  <v-label>密码 :</v-label>
                  <span class="text-caption text-lightText d-block">输入密码</span>
                </v-col>
                <v-col md="7" cols="12" class="pt-md-3 pt-0">
                  <v-text-field single-line variant="outlined" hide-details>
                    <template v-slot:prepend-inner>
                      <img src="@/assets/images/e-commerce/cvv.png" width="20" alt="img" />
                    </template>
                  </v-text-field>
                </v-col>
              </v-row>
              <v-row class="mb-md-n3 mb-n1">
                <v-col md="5" cols="12" class="pb-md-3 pb-1">
                  <v-label>验证码 :</v-label>
                  <span class="text-caption text-lightText d-block">输入验证码</span>
                </v-col>
                <v-col md="7" cols="12" class="pt-md-3 pt-0">
                  <v-text-field single-line variant="outlined" hide-details>
                    <template v-slot:prepend-inner>
                      <img src="@/assets/images/e-commerce/lock.png" width="20" alt="img" />
                    </template>
                  </v-text-field>
                </v-col>
                <v-col cols="12" class="text-right">
                  <v-btn variant="outlined" class="mr-2" color="secondary">取消</v-btn>
                  <v-btn variant="flat" color="primary">保存</v-btn>
                </v-col>
                <v-col cols="12" class="d-flex align-center">
                  <v-divider />
                  <div class="px-2">***</div>
                  <v-divider />
                </v-col>
              </v-row>
            </v-card-item>
            <v-card-text class="mt-4 px-0 pb-0">
              <v-row>
                <v-col cols="12" sm="6" lg="5">
                  <v-card elevation="0" variant="outlined" class="object-card overflow-hidden">
                    <v-card-text class="top-object">
                      <div class="d-flex mb-12">
                        <div>
                          <h5 class="text-h5 mb-0">江方奇</h5>
                          <h6 class="text-h5">137508272419</h6>
                        </div>
                        <div class="ml-auto">
                          <img src="@/assets/images/e-commerce/mastercard.png" width="42" alt="img" />
                        </div>
                      </div>

                      <div class="d-flex align-center justify-space-between mt-3">
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">支付宝</span>
                          <span class="text-caption d-block"></span>
                        </div>
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">上一次支付时间</span>
                          <span class="text-caption d-block">2/22</span>
                        </div>
                      </div>
                    </v-card-text>
                  </v-card>
                </v-col>
                <v-col cols="12" sm="6" lg="5">
                  <v-card elevation="0" variant="outlined" class="object-card overflow-hidden">
                    <v-card-text class="top-object">
                      <div class="d-flex mb-12">
                        <div>
                          <h5 class="text-h5 mb-0">朱钱宁</h5>
                          <h6 class="text-h5">19875481124</h6>
                        </div>
                        <div class="ml-auto">
                          <img src="@/assets/images/e-commerce/visa.png" width="24" alt="img" />
                        </div>
                      </div>

                      <div class="d-flex align-center justify-space-between mt-3">
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">微信</span>
                          <span class="text-caption d-block"></span>
                        </div>
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">上一次支付时间</span>
                          <span class="text-caption d-block">3/25</span>
                        </div>
                      </div>
                    </v-card-text>
                  </v-card>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
          <v-card elevation="0" variant="text" v-if="payment == 'cash'" disabled>
            <v-card-item class="py-3 px-0">
              <v-row class="mb-md-n3 mb-n1">
                <v-col cols="12" class="d-flex align-center">
                  <v-divider />
                  <div class="px-2">***</div>
                  <v-divider />
                </v-col>
              </v-row>
            </v-card-item>
            <v-card-text class="mt-4 px-0 pb-0">
              <v-row>
                <v-col cols="12" sm="6" lg="5">
                  <v-card elevation="0" variant="outlined" class="object-card overflow-hidden">
                    <v-card-text class="top-object">
                      <div class="d-flex mb-12">
                        <div>
                          <h5 class="text-h5 mb-0">江方奇</h5>
                          <h6 class="text-h5">137508272419</h6>
                        </div>
                        <div class="ml-auto">
                          <img src="@/assets/images/e-commerce/mastercard.png" width="42" alt="img" />
                        </div>
                      </div>

                      <div class="d-flex align-center justify-space-between mt-3">
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">支付宝</span>
                          <span class="text-caption d-block"></span>
                        </div>
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">上一次支付时间</span>
                          <span class="text-caption d-block">10/22</span>
                        </div>
                      </div>
                    </v-card-text>
                  </v-card>
                </v-col>
                <v-col cols="12" sm="6" lg="5">
                  <v-card elevation="0" variant="outlined" class="object-card overflow-hidden">
                    <v-card-text class="top-object">
                      <div class="d-flex mb-12">
                        <div>
                          <h5 class="text-h5 mb-0">朱钱宁</h5>
                          <h6 class="text-h5">19875481124</h6>
                        </div>
                        <div class="ml-auto">
                          <img src="@/assets/images/e-commerce/visa.png" width="24" alt="img" />
                        </div>
                      </div>

                      <div class="d-flex align-center justify-space-between mt-3">
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">微信</span>
                          <span class="text-caption d-block"></span>
                        </div>
                        <div class="d-flex align-center">
                          <span class="text-medium-emphasis text-caption opacity-50 mr-2">上一次支付时间</span>
                          <span class="text-caption d-block">3/25</span>
                        </div>
                      </div>
                    </v-card-text>
                  </v-card>
                </v-col>
              </v-row>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>
<style lang="scss">
.object-card {
  position: relative;
  background-color: rgb(var(--v-theme-containerBg));
}
html .label-op-1 label {
  opacity: 1 !important;
}
</style>
