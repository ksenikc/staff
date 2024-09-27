<script setup>
import { ref } from 'vue';

// Создаем реактивные переменные для хранения данных
const items = ref([]);
const newItem = ref({
  tabNumber: '',
  fullName: '',
  email: '',
  phone: '',
  position: ''
});

// Функция для добавления данных
const addData = () => {
  items.value.push({ ...newItem.value });
  newItem.value = {
    tabNumber: '',
    fullName: '',
    email: '',
    phone: '',
    position: ''
  };
};
const Delete = (index) => {
  
    items.value.splice(index, 1);
  
}
</script>

<template>
  <div class="wrapper">
    <header >
        <h2>Staff</h2>
      <ul class="nav nav-pills">
        <li class="nav-item"><a href="#" class="nav-link active" aria-current="page">Главная</a></li>
        <li class="nav-item"><a href="#" class="nav-link">Распорядок</a></li>
        <li class="nav-item"><a href="#" class="nav-link">Добавить</a></li>
      </ul>
    </header>
    <h1>Список сотрудников</h1>
    <div class="container">
      <div class="row mb-3 text-center">
        <div class="col-2 themed-grid-col">Таб номер</div>
        <div class="col-3 themed-grid-col">ФИО</div>
        <div class="col-2 themed-grid-col">Email</div>
        <div class="col-2 themed-grid-col">Телефон</div>
        <div class="col-2 themed-grid-col">Должность</div>
      </div>
      <div class="row mb-3 text-center" v-for="(item, index) in items" :key="index">
        <div class="col-2 themed-grid-col">{{ item.tabNumber }}</div>
        <div class="col-3 themed-grid-col">{{ item.fullName }}</div>
        <div class="col-2 themed-grid-col">{{ item.email }}</div>
        <div class="col-2 themed-grid-col">{{ item.phone }}</div>
        <div class="col-2 themed-grid-col">{{ item.position }}</div>
        <div class="col-1 themed-grid-col"><button type="button" class="btn btn-danger" @click="Delete(index)">Удалить</button></div>
      </div>
    </div>

    <div class="container">
      <form action="" class="form">
        <input type="text" class="form-control" v-model="newItem.tabNumber" placeholder="Таб номер">
        <input type="text" class="form-control" v-model="newItem.fullName" placeholder="ФИО">
        <input type="email" class="form-control" v-model="newItem.email" placeholder="Email">
        <input type="text" class="form-control" v-model="newItem.phone" placeholder="Телефон">
        <select class="form-select" v-model="newItem.position">
          <option value="Менеджер">Менеджер</option>
          <option value="Программист">Программист</option>
          <option value="Администратор">Администратор</option>
        </select>

        <button type="button" @click="addData" class="btn btn-primary">Сохранить</button>
      </form>
    </div>

  </div>
</template>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-top: 20px;
  padding-left: 40px;
}

.form-control, .form-select {
  width: 100%;
}
header {
  float: left;
  height: 500px;
  justify-content: center;
  width: 250px;
}
h1 {
  background-color: rgb(228, 228, 112);
  height: 75px;
  padding-top: 10px;
  padding-left: 300px;
}
a {
  width: 100px;
  margin-left: 50px;
}
h2 {
  height: 30px;
  padding-left: 80px;
  margin-top: 20px;
}
ul {
  display: block;
  margin-top: 200px;
}
.container {
  margin-top: 40px;
  margin-left: 100px;
}
</style>