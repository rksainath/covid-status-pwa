<template>
  <ion-grid>
    <form>
      <ion-item>
        <ion-label>Select Country</ion-label>
      </ion-item>
      <ion-select v-bind="selected" :value="country" @input="country = $event.target.value" name="country" v-on:ionChange="OnSubmit">
        <ion-select-option value="IND">INDIA</ion-select-option>
        <ion-select-option value="USA">USA</ion-select-option>
      </ion-select>
    </form>
  </ion-grid>
</template>

<script>
export default {
  name: "CovidSelect",
  data() {
    return {
      country: ""
    };
  },
  methods: {
    OnSubmit(e) {
      e.preventDefault();
      this.$emit("get-country", this.country);
      this.country = "";
    }
  }
};
</script>
