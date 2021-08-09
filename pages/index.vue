<template>
  <div id="main">
    <div id="video">
      <video ref="spaceVideo" autoplay muted id="bgVideo">
        <source src="~/assets/images/main.mp4" type="video/mp4">
      </video>
    </div>
    <b-container>
        <b-row >
          <b-col>
            <Landing :videoPaused="videoPaused" style="height:100vh" />
          </b-col>
        </b-row>
        <b-row id="services" class="mt-5">
          <b-col>
            <Services />
          </b-col>
        </b-row>
        <b-row class="mt-5">
          <b-col>
            <OurProcess />
          </b-col>
        </b-row>
        <b-row class="mt-5">
          <b-col>
            <FAQ />
          </b-col>
        </b-row>
        <b-row id="contact" class="mt-5">
          <b-col>
            <ContactUs />
          </b-col>
        </b-row>
    </b-container>
  </div>
</template>

<script>

export default {
  data() {
    return {
      videoEl: null,
      videoPaused: false
    }
  },
  mounted() {
    this.videoEl = this.$refs["spaceVideo"];
    this.videoEl.addEventListener("timeupdate", this.onTimeUpdate)
  },
  beforeDestroy() {
    this.videoEl.removeEventListener("timeupdate", this.onTimeUpdate);
  },

  methods: {
    onTimeUpdate(e) {
      if (this.videoEl.duration - this.videoEl.currentTime < 0.5) {
          this.videoEl.pause();
          this.videoPaused = true;
          this.videoEl.classList.add("dim");
        }
    }
  }

}
</script>

<style>
  #main {
    /* background-image: url("~/assets/images/landing-lg.png"); */
    /* background-position: top; */
    background-size: contain;
    background-repeat: no-repeat;
    background-color: #040004;
  }

  #video {
    position: fixed;
    right: 0;
    bottom: 0;
    min-width: 100%;
    min-height: 100%;
  }

  #bgVideo {
    min-width: 100%;
    min-height: 100vh;
  }

</style>
