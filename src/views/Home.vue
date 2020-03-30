<!--Source: API for Current cases and more stuff about COVID-19 or the Novel Coronavirus Strain https://github.com/NovelCOVID/API -->

<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>
          <div class="heading">COVID-19 Status</div>
        </ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <CovidSelect v-on:get-country="getCountryStatus" />
      <CovidInfo v-bind:info="info" />
    </ion-content>
    <ion-footer>
      <ion-toolbar>
        <ion-title>
          <div class="footer">
            <a :href="'//' + 'github.com/rksainath/covid-status-pwa'" target="_blank">
              <ion-icon name="logo-github" style="zoom:2;"></ion-icon>
            </a>
          </div>
        </ion-title>
      </ion-toolbar>
    </ion-footer>
  </div>
</template>

<script>
import CovidSelect from "../components/CovidSelect";
import CovidInfo from "../components/CovidInfo";

export default {
  name: "Home",
  components: { CovidSelect, CovidInfo },
  data() {
    return {
      info: null
    };
  },
  methods: {
    async getCountryStatus(country) {
      if (country && country !== '') {
        const res = await fetch(
          `https://corona.lmao.ninja/countries/${country}`
        );
        if (res.status == 404) {
          this.info = null;
          this.showAlert();
        } else {
          this.info = await res.json();
        }
      } else {
        this.info = null;
      }
    },
    showAlert() {
      return this.$ionic.alertController
        .create({
          header: "Not Valid",
          message: "Please enter a valid country code",
          buttons: ["OK"]
        })
        .then(a => a.present());
    }
  }
};
</script>
<style>
.heading {
  font-size: 1.4em;
  text-align: center;
  font-weight: bold;
  color: #335bff;
}
.footer {
  font-size: 0.8em;
  text-align: center;
}
</style>
