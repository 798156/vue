<script setup lang="ts">
import { ref } from 'vue';
import { useContactStore } from '@/stores/apps/contact';
import User1 from '@/assets/images/users/avatar-1.png';

// icons
import { UserOutlined, BankOutlined, WalletOutlined, MailOutlined, PhoneOutlined, CalendarOutlined } from '@ant-design/icons-vue';

const store = useContactStore();

const birthday = ref('11月 29, 2025');
const uploader = ref();
const selectedFile = ref('');
function onButtonClick() {
  uploader.value.click();
}
function onFileChanged(e: Event) {
  const inputElement = e.target as HTMLInputElement;
  const file = inputElement.files?.[0];
  selectedFile.value = file ? file.name : '';
}
const contact = ref({
  name: '',
  company: '',
  role: '',
  work_email: '',
  personal_email: '',
  work_phone: '',
  personal_phone: '',
  location: '浙江',
  avatar: User1,
  status: '在线',
  lastMessage: '2小时前',
  birthdayText: ''
});
const handleOnAdd = () => {
  store.addContacts(contact.value);
  contact.value = {
    name: '',
    company: '',
    role: '',
    work_email: '',
    personal_email: '',
    work_phone: '',
    personal_phone: '',
    location: '浙江',
    avatar: User1,
    status: '在线',
    lastMessage: '2小时前',
    birthdayText: ''
  };
};
</script>

<template>
  <div v-if="contact" class="pa-6">
    <div class="d-flex align-center">
      <img :src="contact.avatar" :alt="contact.avatar" width="48" class="mr-2 rounded-md" />
      <div>
        <v-btn color="primary" size="small" variant="outlined" @click="onButtonClick">更改头像</v-btn>
        <input ref="uploader" class="d-none" type="file" accept="image/*" @change="onFileChanged" />
      </div>
    </div>
    <form class="my-5">
      <div class="py-3">
        <v-text-field variant="outlined" v-model="contact.name" single-line label="Name" hide-details color="primary">
          <template v-slot:prepend-inner>
            <UserOutlined class="text-lightText" :style="{ fontSize: '20px' }" />
          </template>
        </v-text-field>
      </div>
      <div class="py-3">
        <v-text-field variant="outlined" v-model="contact.company" single-line label="Company" hide-details color="primary">
          <template v-slot:prepend-inner>
            <BankOutlined class="text-lightText" :style="{ fontSize: '20px' }" />
          </template>
        </v-text-field>
      </div>
      <div class="py-3">
        <v-text-field variant="outlined" v-model="contact.role" label="Job Title" hide-details single-line color="primary">
          <template v-slot:prepend-inner>
            <WalletOutlined class="text-lightText" :style="{ fontSize: '20px' }" />
          </template>
        </v-text-field>
      </div>
      <div class="py-3">
        <v-text-field variant="outlined" v-model="contact.work_email" label="Mail" hide-details single-line color="primary">
          <template v-slot:prepend-inner>
            <MailOutlined class="text-lightText" :style="{ fontSize: '20px' }" />
          </template>
        </v-text-field>
      </div>
      <div class="py-3">
        <v-text-field variant="outlined" v-model="contact.work_phone" label="Phone" hide-details single-line color="primary">
          <template v-slot:prepend-inner>
            <PhoneOutlined class="text-lightText" :style="{ fontSize: '20px' }" />
          </template>
        </v-text-field>
      </div>
      <div class="py-3">
        <v-text-field variant="outlined" v-model="birthday" aria-label="birthday" label="Birthday" hide-details single-line color="primary">
          <template v-slot:append-inner>
            <CalendarOutlined class="text-lightText" :style="{ fontSize: '20px' }" />
          </template>
        </v-text-field>
      </div>
      <div class="py-3">
        <v-textarea label="Bio" density="comfortable" single-line variant="outlined" v-model="contact.birthdayText"> </v-textarea>
      </div>
      <div class="py-3 pt-0 d-flex ga-2">
        <v-btn variant="flat" :disabled="contact.name === ''" color="primary" @click="$emit('closeDrawer'), handleOnAdd()"
          >添加联系人</v-btn
        >
        <v-btn variant="outlined" color="secondary" @click="$emit('closeDrawer')">取消</v-btn>
      </div>
    </form>
  </div>
</template>
