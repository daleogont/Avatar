<script lang="ts">
import { defineComponent } from 'vue';
import AvatarUpload from './components/AvatarUpload..vue';

export default defineComponent({
  name: 'App',
  components: {
    AvatarUpload,
  },
});
</script>

<template>
  <div class="h-screen w-screen  bg-pink-100 py-20 px-20">

    
    <div class=" h-full w-full bg-blue-200 rounded py-10 px-10 flex flex-col gap-10">
      <div class=" h-40 bg-yellow-100 rounded flex justify-center items-center">
        <<div class="min-h-screen flex items-center justify-center">
           <AvatarUpload />
        </div>
      </div>
      <div class=" h-15 bg-green-200 rounded">box2</div>
      <div class=" h-15 bg-yellow-100 rounded">box3</div>
      <div class=" h-15 bg-green-200 rounded">box4</div>
      <div class=" h-15 bg-yellow-100 rounded">box5</div>
    </div>
   
  </div>

</template>

<style scoped>

</style>
