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
    IonButton,
    IonSelect,
    IonSelectOption
} from '@ionic/vue';
import { ref, onMounted } from 'vue';
import axios from 'axios';

const contactos = ref([]);

function deleteItem(id: number) {
    contactos.value = contactos.value.filter((item) => item.id !== id);
}
function onChange(event: any) {
    console.log(event.detail.value);
}

async function getDatos(){
    
   const datos = await axios.get('https://jsonplaceholder.typicode.com/users');
    contactos.value = datos.data;
   
}

onMounted(() => {
    getDatos();
});

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
            <ion-select @ionChange="onChange($event)">
                <ion-select-option value="1">One</ion-select-option>
                <ion-select-option value="2">Two</ion-select-option>
                <ion-select-option value="3">Three</ion-select-option>
            </ion-select>
        </ion-content>
    </ion-page>

</template>