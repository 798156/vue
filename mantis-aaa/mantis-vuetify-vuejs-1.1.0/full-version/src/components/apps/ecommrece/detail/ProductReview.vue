<script setup lang="ts">
import { ref, shallowRef } from 'vue';
import user1 from '@/assets/images/users/avatar-1.png';
import user2 from '@/assets/images/users/avatar-2.png';
import user3 from '@/assets/images/users/avatar-3.png';

// icons
import { VideoCameraAddOutlined, FileAddOutlined, SmileOutlined } from '@ant-design/icons-vue';

type commentsType = {
  name: string;
  desc: string;
  avatar: string;
  date: string;
  ratings: number;
};
const rating = ref(4);
const comments = shallowRef<commentsType[]>([
  {
    name: '鲍泽坤',
    desc: '这批有机蔬菜真是太新鲜了，叶子翠绿，口感清脆，我和家里人吃得很放心。❤',
    avatar: user1,
    date: '02/11, 2025 3:02:24 下午',
    ratings: 3.5
  },
  {
    name: '刘畅',
    desc: '这款五谷杂粮包真的很实用，里面包含了多种不同的谷物，煮出来的粥口感非常好，全家人都喜欢。我购买的有机糙米质量非常好，米粒饱满，煮出来的米饭香气扑鼻，非常有嚼劲。',
    avatar: user2,
    date: '28/10, 2024 4:28:24 上午',
    ratings: 1.5
  },
  {
    name: '黄逸一',
    desc: '这款绿茶的味道非常清新，泡出来的茶水色泽碧绿，喝起来让人感到心旷神怡。我送给父亲的绿茶，他非常喜欢，说这款茶的口感醇厚，回味悠长。',
    avatar: user3,
    date: '25/3, 2025 11:25:24 上午',
    ratings: 5
  }
]);
</script>

<template>
  <v-row>
    <v-col lg="12" cols="12">
      <v-card variant="outlined" elevation="0" class="h-100 d-flex align-center justify-center">
        <v-row class="mx-0 align-center">
          <v-col cols="12" md="5" sm="4" class="pa-sm-4">
            <div class="pt-sm-0 pt-5">
              <h2 class="text-h2 mb-2 d-flex align-center">
                4
                <h4 class="text-h4 text-lightText mb-0 ml-1">/5</h4>
              </h2>
              <p class="text-h6 text-lightText mb-1">基于275位用户的评分</p>
              <div class="text-medium-emphasis align-center d-flex ga-2">
                <v-rating color="inputBorder" active-color="warning" half-increments v-model="rating" density="compact"> </v-rating>
              </div>
            </div>
          </v-col>
          <v-col cols="12" md="7" sm="8" class="pa-sm-4">
            <div class="pa-sm-4">
              <div class="d-flex align-center ga-4 my-2">
                <v-progress-linear
                  model-value="100"
                  aria-label="progressbar"
                  height="6"
                  color="warning"
                  bg-color="gray100"
                  bg-opacity="1"
                  rounded
                ></v-progress-linear>
                <div class="text-no-wrap text-caption text-lightText">5星</div>
              </div>
              <div class="d-flex align-center ga-4 my-2">
                <v-progress-linear
                  model-value="80"
                  aria-label="progressbar"
                  height="6"
                  color="warning"
                  bg-color="gray100"
                  bg-opacity="1"
                  rounded
                ></v-progress-linear>
                <div class="text-no-wrap text-caption text-lightText">4星</div>
              </div>
              <div class="d-flex align-center ga-4 my-2">
                <v-progress-linear
                  model-value="60"
                  aria-label="progressbar"
                  height="6"
                  color="warning"
                  bg-color="gray100"
                  bg-opacity="1"
                  rounded
                ></v-progress-linear>
                <div class="text-no-wrap text-caption text-lightText">3星</div>
              </div>
              <div class="d-flex align-center ga-4 my-2">
                <v-progress-linear
                  model-value="40"
                  aria-label="progressbar"
                  height="6"
                  color="warning"
                  bg-color="gray100"
                  bg-opacity="1"
                  rounded
                ></v-progress-linear>
                <div class="text-no-wrap text-caption text-lightText">2星</div>
              </div>
              <div class="d-flex align-center ga-4 my-2">
                <v-progress-linear
                  model-value="20"
                  aria-label="progressbar"
                  height="6"
                  color="warning"
                  bg-color="gray100"
                  bg-opacity="1"
                  rounded
                ></v-progress-linear>
                <div class="text-no-wrap text-caption text-lightText">1星</div>
              </div>
            </div>
          </v-col>
        </v-row>
      </v-card>
    </v-col>
    <v-col lg="12">
      <v-card variant="outlined" class="d-flex align-center mb-7 bg-containerBg" v-for="(comment, i) in comments" :key="i">
        <div class="d-flex align-start ga-2 pa-4">
          <v-avatar size="40">
            <img :src="comment.avatar" alt="users" width="40" />
          </v-avatar>
          <div>
            <h6 class="text-subtitle-1 mb-0">{{ comment.name }}</h6>
            <span class="text-caption text-lightText">{{ comment.date }}</span>
            <div class="v-col-lg-2 px-0 py-0">
              <v-rating
                size="small"
                half-increments
                v-model="comment.ratings"
                density="compact"
                color="inputBorder"
                active-color="warning"
              />
            </div>
            <p class="text-caption mt-2">{{ comment.desc }}</p>
          </div>
        </div>
      </v-card>
    </v-col>
  </v-row>
  <div class="text-center mb-6">
    <v-btn variant="text" color="primary">浏览更多的评论(2k+)</v-btn>
  </div>
  <div class="position-relative">
    <v-textarea density="comfortable" hide-details placeholder="添加评论" variant="outlined"></v-textarea>
    <div class="comment-panel d-flex justify-space-between align-center pa-3">
      <div>
        <v-btn icon rounded color="primary" variant="text">
          <VideoCameraAddOutlined />
        </v-btn>
        <v-btn icon rounded color="primary" variant="text">
          <FileAddOutlined />
        </v-btn>
        <v-btn icon rounded color="primary" variant="text">
          <SmileOutlined />
        </v-btn>
      </div>
      <v-btn color="primary" variant="flat" size="small">评论</v-btn>
    </div>
  </div>
</template>
<style lang="scss">
.comment-panel {
  position: absolute;
  bottom: 0;
  width: 100%;
}
</style>
