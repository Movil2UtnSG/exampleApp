<script setup lang="ts">
import {
    IonPage,
    IonHeader,
    IonToolbar,
    IonButtons,
    IonMenuButton,
    IonTitle,
    IonContent
} from '@ionic/vue';
</script>
<template>
    <ion-page>
        <ion-header :translucent="true">
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-menu-button color="primary"></ion-menu-button>
                </ion-buttons>
                <ion-title>Contact</ion-title>
            </ion-toolbar>
        </ion-header>

        <ion-content :fullscreen="true">
            <h1>Contact</h1>
        </ion-content>
    </ion-page>

</template>