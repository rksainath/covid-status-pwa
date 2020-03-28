<template>
  <ion-card v-if="info">
    <ion-card-header>
      <ion-card-subtitle>
        <ion-thumbnail>
          <ion-img style="width: 35px; height: 30px;" :src="info.countryInfo.flag"></ion-img>
        </ion-thumbnail>
      </ion-card-subtitle>
      <ion-card-title>{{info['country']}}</ion-card-title>

      <ion-card-content>
        <ion-list>
          <ion-item>
            <ion-label>
              <span class="cases">Cases: {{info['cases']}}</span>
            </ion-label>
          </ion-item>
          <ion-item>
            <ion-label>
              <span class="deaths">Deaths: {{info['deaths']}}</span>
            </ion-label>
          </ion-item>
          <ion-item>
            <ion-label>
              <span class="recovered">Recovered: {{info['recovered']}}</span>
            </ion-label>
          </ion-item>
          <ion-item>
            <ion-label>
              <span class="active">Active: {{info['active']}}</span>
            </ion-label>
          </ion-item>
          <ion-item>
            <ion-label>
              <span class="critical">Critical: {{info['critical']}}</span>
            </ion-label>
          </ion-item>
          <ion-item>
            <ion-label>
              <span class="todaycase">Cases Today: {{info['todayCases']}}</span>
            </ion-label>
          </ion-item>
          <ion-item>
            <ion-label>
              <span class="todaydeath">Deaths Today: {{info['todayDeaths']}}</span>
            </ion-label>
          </ion-item>
        </ion-list>
      </ion-card-content>
    </ion-card-header>
  </ion-card>
</template>

<script>
export default {
  name: "CovidInfo",
  props: ["info"]
};
</script>

<style>
.cases {
  font-size: 1.3em;
  font-weight: bold;
  color: #335bff;
}
.deaths {
  font-size: 1.3em;
  font-weight: bold;
  color: #ff0000;
}
.recovered {
  font-size: 1.3em;
  font-weight: bold;
  color: #349504;
}
.active {
  font-size: 1.3em;
  font-weight: bold;
  color: #0450a7;
}
.critical {
  font-size: 1.3em;
  font-weight: bold;
  color: #fd6c08;
}
.todaycase {
  font-size: 1.3em;
  font-weight: bold;
  color: #000000;
}
.todaydeath {
  font-size: 1.3em;
  font-weight: bold;
  color: #ff0000;
}
</style>