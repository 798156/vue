<script setup lang="ts">
import { ref } from 'vue';
import { useEditor, EditorContent } from '@tiptap/vue-3';
import StarterKit from '@tiptap/starter-kit';
import EditorMenubar from '@/components/forms/plugins/editor/EditorMenubar.vue';

// icons
import { CloseOutlined, UploadOutlined, PaperClipOutlined } from '@ant-design/icons-vue';

const ccBcc = ref(false);
const editor = useEditor({
  extensions: [StarterKit],
  content: ``
});
</script>
<template>
  <v-card elevation="0">
    <v-card-item class="pb-2">
      <div class="d-flex align-center">
        <h4 class="mb-0">新消息</h4>
        <v-btn icon size="small" color="primary" variant="text" class="ml-auto" elevation="0" @click="$emit('closeDialog')"
          ><CloseOutlined
        /></v-btn>
      </div>
    </v-card-item>
    <v-divider></v-divider>
    <v-card-text class="pb-4">
      <v-row>
        <v-col sm="12" cols="12">
          <p class="text-secondary text-right cursor-pointer" @click="ccBcc = !ccBcc">CC & BCC</p>
        </v-col>
        <v-col sm="12" cols="12">
          <v-text-field single-line required variant="outlined" color="primary" hide-details>
            <template v-slot:prepend-inner>
              <span class="text-secondary">To</span>
            </template>
          </v-text-field>
        </v-col>
        <v-col sm="12" cols="12">
          <v-text-field single-line required variant="outlined" color="primary" hide-details>
            <template v-slot:prepend-inner>
              <span class="text-secondary">Subject</span>
            </template>
          </v-text-field>
        </v-col>
        <v-col sm="12" cols="12" v-if="ccBcc">
          <div>
            <v-text-field label="CC" required variant="outlined" color="primary" hide-details class="mb-5"></v-text-field>
            <v-text-field label="BCC" required variant="outlined" color="primary" hide-details></v-text-field>
          </div>
        </v-col>
        <v-col sm="12" cols="12">
          <div v-if="editor">
            <EditorMenubar :editor="editor" />
          </div>
          <editor-content :editor="editor" />
        </v-col>
        <v-col sm="12" cols="12">
          <div class="d-flex">
            <v-btn icon elevation="0" rounded>
              <UploadOutlined />
            </v-btn>
            <v-btn icon elevation="0" rounded>
              <PaperClipOutlined />
            </v-btn>
            <v-btn elevation="0" color="primary" class="ml-auto">Reply</v-btn>
          </div>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>
