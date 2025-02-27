<script setup lang="ts">
import {
    IonPage,
    IonHeader,
    IonToolbar,
    IonButtons,
    IonMenuButton,
    IonTitle,
    IonContent,
    IonButton,
    useIonRouter,
} from '@ionic/vue';

import { useRoute, useRouter } from 'vue-router';

const route = useRoute();
//const router = useRouter();
const ionRouter = useIonRouter();

   
console.log(route.params.name);

function goBack() {
   // router.go(-1);
   // router.push('/home');
    ionRouter.navigate('/home', 'back', 'replace');
}
</script>
<template>
    <ion-page>
        <ion-header :translucent="true">
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-menu-button color="primary"></ion-menu-button>
                </ion-buttons>
                <ion-title>Profile</ion-title>
            </ion-toolbar>
        </ion-header>

        <ion-content :fullscreen="true">
            <h1>Usuario: {{ route.params.name }}</h1>
            <ion-button color="danger" size="large" fill="outline" @click="goBack()">Back</ion-button>
        </ion-content>
    </ion-page>

</template>