<script setup lang="ts">
import { shallowRef } from 'vue';
// icons
import { ArrowRightOutlined } from '@ant-design/icons-vue';

// assets
import imageChart from '@/assets/images/mega-menu/chart.svg';

// to-do all link changes
const dropdownMenu = shallowRef([
  { header: 'Authentication' },
  { header: 'Other pages' },
  { header: 'SASS Pages' },
  {
    link: 'Login',
    href: 'https://mantisdashboard.io/vue/auth/login1'
  },
  {
    link: 'FAQs',
    href: 'https://mantisdashboard.io/vue/pages/faq'
  },
  {
    link: '404 Error',
    href: 'https://mantisdashboard.io/vue/pages/error'
  },
  {
    link: 'Register',
    href: 'https://mantisdashboard.io/vue/auth/register1'
  },
  {
    link: 'Contact us',
    href: 'https://mantisdashboard.io/vue/pages/contact-us'
  },
  {
    link: 'Landing',
    href: 'https://mantisdashboard.io/vue'
  },
  {
    link: 'Reset Password',
    href: 'https://mantisdashboard.io/vue/auth/reset-pwd1'
  },
  {
    link: 'Pricing',
    href: 'https://mantisdashboard.io/vue/pages/pricing1'
  },
  {},
  {
    link: 'Forgot Password',
    href: 'https://mantisdashboard.io/vue/auth/forgot-pwd1'
  },
  {
    link: 'Privacy policy',
    href: 'https://mantisdashboard.io/vue/pages/privacy-policy'
  },
  {},
  {
    link: 'Verification code',
    href: 'https://mantisdashboard.io/vue/auth/code-verify1'
  },
  {
    link: 'Construction',
    href: 'https://mantisdashboard.io/vue/pages/construction'
  },
  {},
  {},
  {
    link: 'Coming soon',
    href: 'https://mantisdashboard.io/vue/pages/comingsoon1'
  }
]);
function openNewTab() {
  const url = 'https://mantisdashboard.io/vue/components/buttons'; // Replace with your URL
  window.open(url, '_blank');
}
</script>

<template>
  <!-- ---------------------------------------------- -->
  <!-- mega menu DD -->
  <!-- ---------------------------------------------- -->
  <div>
    <v-row class="ma-0">
      <v-col cols="12" lg="4" class="pa-0">
        <div class="megamenu-banner pa-9">
          <h2 class="text-h2 text-white mb-1">Explore Components</h2>
          <p class="text-h6 text-white mb-0">Try our pre made component pages to check how it feels and suits as per your need.</p>
          <div class="d-flex justify-between align-end">
            <v-btn @click="openNewTab" variant="flat" class="scale-hover">
              View All
              <ArrowRightOutlined class="ml-1" />
            </v-btn>
            <v-img :src="imageChart" alt="chart" width="124" height="126" />
          </div>
        </div>
      </v-col>
      <v-col cols="12" lg="8" class="pa-0">
        <v-list density="compact" class="overflow-hidden pt-6 px-4" aria-label="mega menu list" aria-busy="true">
          <v-row no-gutters>
            <template v-for="(item, i) in dropdownMenu" :key="i">
              <v-col cols="6" sm="4">
                <v-list-item v-if="item.header" rounded="md">
                  <v-list-item-title class="text-subtitle-1">{{ item.header }}</v-list-item-title>
                </v-list-item>
                <v-list-item
                  v-if="item.link"
                  :href="item.href"
                  rounded="md"
                  variant="plain"
                  color="secondary"
                  target="_blank"
                  class="no-spacer"
                >
                  <template v-slot:prepend>
                    <v-icon class="text-8 mr-4 text-lightText" icon="$circleOutline"></v-icon>
                  </template>
                  <v-list-item-title class="text-subtitle-1 font-weight-regular">{{ item.link }} </v-list-item-title>
                </v-list-item>
              </v-col>
            </template>
          </v-row>
        </v-list>
      </v-col>
    </v-row>
  </div>
</template>

<style lang="scss">
.megamenu-banner {
  background: url('@/assets/images/mega-menu/back.svg'), linear-gradient(183.77deg, #1677ff 11.46%, #003eb3 100.33%);
  height: 100%;
  padding-bottom: 37px !important;
  .d-flex {
    .v-img {
      object-fit: cover;
      margin-right: -60px;
      margin-bottom: -20px;
      width: 124px;
    }
  }
}
.v-btn {
  &.scale-hover {
    &:hover {
      transform: scale(1.05);
    }
  }
}
.v-menu {
  .v-list-item__prepend {
    > .v-icon {
      --v-medium-emphasis-opacity: 1;
    }
  }
  .v-list-item--variant-plain {
    opacity: 1;
    &:hover {
      color: rgb(var(--v-theme-primary));
    }
  }
}
</style>
