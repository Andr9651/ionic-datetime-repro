<template>
  <ion-button id="modal1" expand="block">Open inconsistent</ion-button>
  <ion-modal ref="modal1" trigger="modal1" @willDismiss="onWillDismiss">
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-button @click="cancel1()">Cancel</ion-button>
        </ion-buttons>
        <ion-title>Bad Month-Year</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <ion-datetime
        v-model="computedDate"
        presentation="month-year"
      ></ion-datetime>
    </ion-content>
  </ion-modal>

  <ion-button id="modal2" expand="block">Open workaround</ion-button>
  <ion-modal
    ref="modal2"
    trigger="modal2"
    :keep-contents-mounted="true"
    @willDismiss="onWillDismiss"
  >
    <ion-header>
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-button @click="cancel2()">Cancel</ion-button>
        </ion-buttons>
        <ion-title>Bad Month-Year</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <ion-datetime
        v-model="computedDate"
        presentation="month-year"
      ></ion-datetime>
    </ion-content>
  </ion-modal>
</template>

<script setup lang="ts">
import {
  IonModal,
  IonHeader,
  IonToolbar,
  IonButtons,
  IonButton,
  IonTitle,
  IonDateTime,
  IonContent,
} from '@ionic/vue';
import { ref, computed } from 'vue';

let date = new ref(new Date());

const computedDate = computed({
  get: () => {
    return date.value.toISOString();
  },
  set: (value) => {
    date.value = new Date(value);
  },
});

const modal1 = ref();
const cancel1 = () => modal1.value.$el.dismiss(null, 'cancel');

const modal2 = ref();
const cancel2 = () => modal2.value.$el.dismiss(null, 'cancel');
</script>
