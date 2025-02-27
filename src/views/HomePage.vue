<script setup lang="ts">
import {
    IonPage,
    IonHeader,
    IonToolbar,
    IonButtons,
    IonMenuButton,
    IonTitle,
    IonContent,
    IonList,
    IonItem,
    IonAvatar,
    IonLabel,
    IonButton
} from '@ionic/vue';
import { ref } from 'vue';

const contactos = ref([
    { name: 'Huey', id: 1, img: 'https://ui-avatars.com/api/?name=Huey' },
    { name: 'Dewey', id: 2, img: 'https://ui-avatars.com/api/?name=Dewey' },
    { name: 'Louie', id: 3, img: 'https://ui-avatars.com/api/?name=Louie' },
    { name: 'Fooie', id: 4, img: 'https://ui-avatars.com/api/?name=Fooie' }
]);

function deleteItem(id: number) {
    contactos.value = contactos.value.filter((item) => item.id !== id);
}
</script>
<template>
    <ion-page>
        <ion-header :translucent="true">
            <ion-toolbar>
                <ion-buttons slot="start">
                    <ion-menu-button color="primary"></ion-menu-button>
                </ion-buttons>
                <ion-title>Home</ion-title>
            </ion-toolbar>
        </ion-header>

        <ion-content :fullscreen="true">
            <h1>Home</h1>
            <ion-list>
                <ion-item v-for="item in contactos" :key="item.id" >
                    <ion-avatar aria-hidden="true" slot="start">
                        <img alt="" :src="item.img" />
                    </ion-avatar>
                    <ion-label :router-link="'/profile/' + item.name">{{ item.name }}</ion-label>
                    <ion-button color="danger" @click="deleteItem(item.id)">Eliminar</ion-button>
                </ion-item>
               
            </ion-list>
        </ion-content>
    </ion-page>

</template>