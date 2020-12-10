<template>
  <div class="video1">

    
      <!-- <vue-core-video-player controls :src="videoSource"></vue-core-video-player> -->
    <video-player  
                 class="video-player-box"
                 ref="videoPlayer"
                 reset
                 :options="playerOptions"
                 :playsinline="true"
                 @ended="onPlayerEnded($event)"
                 customEventName="customstatechangedeventname"
                 @ready="playerReadied">
  </video-player>
  </div>
</template>
<script>

  import VuePlaylist from 'vue-playlist';
  // Similarly, you can also introduce the plugin resource pack you want to use within the component
  // import 'some-videojs-plugin'
  export default {
    data() {
      return {
        videos: {
          type: "video/mp4",
          src: './video/1.mp4'
        },
        videoSource :[
            {
              src: 'https://media.vued.vanthink.cn/sparkle_your_name_am360p.mp4',
              resolution: '360p',
            }, {
              src: 'https://media.vued.vanthink.cn/sparkle_your_name_am720p.mp4',
              resolution: '720p',
            }, {
              src: 'https://media.vued.vanthink.cn/y2mate.com%20-%20sparkle_your_name_amv_K_7To_y9IAM_1080p.mp4',
              resolution: '1080p'
            }
          ],

        playerOptions: {
          // videojs options
          
          fluid: true,
          language: 'es',
          // autoplay: true,
          // loop:true,
          playbackRates: [0.7, 1.0, 1.5, 2.0],
          sources: [
            {
              type: "video/mp4",
              src: './video/1.mp4'
            }
          ],
          sources: [
            {
              type: "video/mp4",
              src: './video/2.mp4'
            }
          ],
          
        }
      }
    },
    mounted() {
      
      console.log('this is current player instance object', this.player)
    },
    computed: {
      player() {
        return this.$refs.videoPlayer.player
      }
    },
    methods: {
      
      // listen event
      onPlayerPlay(player) {
        // console.log('player play!', player)
      },
      onPlayerEnded(player) {
        console.log('player end!', player)
      },
      // ...player event

      // or listen state event
      playerStateChanged(playerCurrentState) {
        // console.log('player current update state', playerCurrentState)
      },

      // player is ready
      playerReadied(player) {
        console.log('the player is readied', player)
        // you can use it to do something...
        // player.[methods]
      }
    }
  }
</script>