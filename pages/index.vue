<template>
  <div id="main">
    <b-container>
        <b-row>
          <b-col>
            <Landing />
          </b-col>
        </b-row>
        <b-row id="services">
          <b-col>
            <Services />
          </b-col>
        </b-row>
        <b-row>
          <b-col>
            <OurProcess />
          </b-col>
        </b-row>
        <b-row>
          <b-col>
            <FAQ />
          </b-col>
        </b-row>
        <b-row id="contact">
          <b-col>
            <ContactUs />
          </b-col>
        </b-row>
    </b-container>
  </div>
</template>

<script>

export default {

}
</script>

<style>
  #main {
    background-image: url("~/assets/images/landing-lg.png");
    /* background-position: top; */
    background-size: contain;
    background-repeat: no-repeat;
    background-color: #040004;
  }

</style>
