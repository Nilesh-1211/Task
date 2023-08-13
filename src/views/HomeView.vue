<template>
  <v-app>
    <v-main>
      <div class="d-flex align-center mx-auto fill-height" 
      :style="{width: '60%'}">
      <video_player/>
        <!-- <slider :value=".75"/> -->
    </div>
    </v-main>
  </v-app>
</template>

<script>
  import video_player from '@/components/video_player/video_player.vue';
  /* import slider from '@/components/slider/slider.vue'; */

  export default {
    name: 'Home',
    components:{
      video_player
      /* slider */
    }
    
  }
</script>
