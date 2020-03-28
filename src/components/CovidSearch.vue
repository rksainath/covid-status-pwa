<template>
    <ion-grid>
        <form @submit="OnSubmit">
            <ion-col>
                <ion-item>
                    <ion-label>Search for the Country:</ion-label>
                    <ion-input :value="country" @input="country = $event.target.value" placeholder="Enter IND for" name='country'></ion-input>
                </ion-item>
            </ion-col>
            <ion-col>
                <ion-button type='submit' color='primary' expand='block' round>Find</ion-button>
            </ion-col>
        </form>
    </ion-grid>    
</template>

<script>
export default {
    name: "CovidSearch",
    data(){
        return {
            country:""
        }
    },
    methods: {
        OnSubmit(e){
            e.preventDefault();
            this.$emit("get-country", this.country)
            this.country=""
        }
    }
    
}
</script>
