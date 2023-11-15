<script setup>
import { ref } from 'vue';


const newCard = ref('')

const card = ref([{nombreEvento:'', nombreInvitado:'', edad: 0, telefono:'' }])


const addCard = () => {
  
  card.value.forEach(carta => {
    card.value.push({nombreEvento: carta.nombreEvento, nombreInvitado: carta.nombreInvitado, edad: carta.edad, telefono: carta.telefono})

    carta.nombreEvento = '';
    carta.nombreInvitado = '';
    carta.edad = 0;
    carta.telefono = '';
  });

  
 
}
const clearFields = () => {
  // Limpiar los campos del formulario
  card.value.forEach(carta => {
    carta.nombreEvento = '';
    carta.nombreInvitado = '';
    carta.edad = 0;
    carta.telefono = '';
  });
};

</script>



<template>
  <div>
       <div v-for="(carta, index) in card" :key="index">
          <p>Nombre del evento:  <span >{{ carta.nombreEvento }}</span></p>
          <p>Nombre del invitado:  <span></span>{{ carta.nombreInvitado }}</p>
          <p>Edad:  <span>{{ carta.edad }}</span></p>
          <p>Numero telefonico:  <span>{{ carta.telefono }}</span></p>
          <p v-show="carta.edad < 18"> <span> El invitado necesita acompañante</span></p>

          <div>
            <input v-model="carta.nombreEvento" type="text" placeholder="Nombre del evento">
            <input v-model="carta.nombreInvitado" type="text" placeholder="Nombre del invitado">
            <input v-model="carta.edad" type="number" placeholder="Edad">
            <input v-model="carta.telefono" type="text" placeholder="Numero telefonico">
            <button @click="addCard">Agregar Tarjeta</button>
            <button @click="clearFields">Limpiar Campos</button>
          </div>
       </div> 
  </div>
</template>

<style scoped></style>
