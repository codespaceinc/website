<template>
  <div id="main">
    <div id="video">
      <video ref="spaceVideo" autoplay muted id="myVideo">
        <source src="~/assets/images/main.mp4" type="video/mp4">
      </video>
    </div>
    <b-container>
        <b-row >
          <b-col>
            <Landing style="height:100vh" />
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
  mounted() {
    this.$refs["spaceVideo"].addEventListener("timeupdate", function(e) {
      console.log(this.duration)
      console.log(e.timeStamp)
        if (e.timeStamp > 7500) {
          this.pause();

          this.classList.add("dim");
        }
    })
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

  #myVideo {
    min-width: 100%;
    min-height: 100vh;
  }

  .dim {
    transition: 1s;
    filter: brightness(0.3);
  }

</style>
