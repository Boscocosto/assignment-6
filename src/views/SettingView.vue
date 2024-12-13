<script setup>
import { ref, onMounted } from 'vue';
import { useStore } from '../store';

const store = useStore();

const name = ref(store.name);
const lastName = ref(store.lastName);
const email = ref(store.email);

onMounted(() => {
  name.value = store.name || '';
  lastName.value = store.lastName || '';
  email.value = store.email || ''; 
});

const handleSave = () => {
  store.name = name.value;
  store.lastName = lastName.value;
  store.email = email.value;
};
</script>

<template>
  <div class="background">
    <div class="header">
      <div class="logo">
        <img src="/movie.png" class="logo" />
        <h1>{{ `Hello ${store.name} ${store.lastName}!` }}</h1>
      </div>
      <div class="buttons">
        <button @click="router.push('/cart')" class="button">Cart</button>
        <button @click="router.push('/')" class="button">Logout</button>
      </div>
    </div>
    <div class="setting">
      <div class="form-field">
        <label for="name">First Name:</label>
        <input v-model="name" type="text" id="name" class="input-field" />
      </div>
      <div class="form-field">
        <label for="lastName">Last Name:</label>
        <input v-model="lastName" type="text" id="lastName" class="input-field" />
      </div>
      <div class="form-field">
        <label for="email">Email:</label>
        <input v-model="email" type="email" id="email" class="input-field" disabled />
      </div>
      <button @click="handleSave" class="save-button">Save</button>
    </div>
  </div>
</template>

<style scoped>
.background {
    background-image: url('/popcorn.jpg');
    background-size: cover;
    background-position: center;
    height: 100vh;
}

.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1%;
    background-color: white;
    border: 2px solid rgba(0, 0, 0, 0.8);
    border-radius: 15px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
    margin: 20px;
}

.logo {
    display: flex;
    align-items: center;
}

.logo img {
    height: 50px;
    margin-right: 10px;
}

.buttons {
    display: flex;
    gap: 10px;
}

.button {
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    background-color: #000000;
    color: white;
    transition: background-color 0.3s;
}

.button:hover {
    background-color: #0000008d;
}

.setting {
    display: flex;
    flex-direction: column;
    padding: 20px;
    border-radius: 10px;
    margin-top: 20%;
}
.firstName, .lastName, .email {
    margin-bottom: 15px; /* Space between input fields */
}

.input-field {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    width: 100%; /* Full width */
    box-sizing: border-box; /* Include padding and border in element's total width and height */
}

.changeButton {
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    background-color: #007BFF; /* Bootstrap primary color */
    color: white;
    transition: background-color 0.3s;
}

.changeButton:hover {
    background-color: #0056b3; /* Darker shade on hover */
}
</style>