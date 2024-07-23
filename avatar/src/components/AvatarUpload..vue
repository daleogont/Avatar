  <script lang="ts">
  import { defineComponent, ref } from 'vue';
  import { library } from '@fortawesome/fontawesome-svg-core';
  import { faCamera } from '@fortawesome/free-solid-svg-icons';
  import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';
  
  library.add(faCamera);
  
  export default defineComponent({
    name: 'AvatarUpload',
    components: {
      FontAwesomeIcon,
    },
    setup() {
      const imageUrl = ref<string | ArrayBuffer | null>(null);
  
      const onFileChange = (event: Event) => {
        const file = (event.target as HTMLInputElement).files?.[0];
        if (file) {
          const reader = new FileReader();
          reader.onload = () => {
            imageUrl.value = reader.result;
          };
          reader.readAsDataURL(file);
        }
      };
  
      return {
        imageUrl,
        onFileChange,
      };
    },
  });
  </script>

<template>
    <div class="flex flex-col items-center">
      <div class="relative w-32 h-32 rounded-full overflow-hidden border border-gray-300">
        <img :src="imageUrl" alt="Avatar" class="w-full h-full object-cover" v-if="imageUrl" />
        <div class="w-full h-full flex items-center justify-center text-gray-500" v-else>
          <div class="text-3xl">No Image</div>
        </div>
        <label 
          for="fileInput" 
          class="absolute bottom-0 right-0 mb-2 mr-2 bg-gray-600 rounded-full p-2 hover:bg-gray-700 cursor-pointer"
        >
          <font-awesome-icon icon="camera" class="text-white text-lg" />
        </label>
      </div>
      <input 
        id="fileInput" 
        type="file" 
        @change="onFileChange" 
        class="hidden"
      />
    </div>
  </template>
  
<style scoped>

</style>
