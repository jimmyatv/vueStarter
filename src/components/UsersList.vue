<template>
  <div class="users">
    <h1 :style="{ textAlign: 'center', fontSize: '60px' }">My Kitty cats</h1>
    <input v-model="searchTerm" type="text" name="" placeholder="Search..." id="">
    <p :style="{ margin: 'auto' }">Type here: {{ searchTerm }}</p>
    <div class="wrapperDiv">
      <div v-for="(user, idx) in filteredKitties" :key="idx" class="user">
        <div class="singleUser">
          <div class="userInfo">
            <p><strong :style="{ fontSize: '24px' }">{{ user.id }}</strong></p>
            <p>Name: <span>{{ user.firstName }}</span></p>
            <p>Last Name: <span>{{ user.lastName }}</span></p>
            <hr :style="{ margin: '5px 0' }">
            <p>Birth date: {{ user.birthDate }}</p>
            <p>Age: {{ user.age }}</p>
            <p>Gender: {{ user.gender }}</p>
            <p>Height: {{ user.height }}</p>
            <p>Weight: {{ user.weight }}</p>
            <p>Number: {{ user.phone }}</p>
            <p>Mail: {{ user.email }}</p>
            <p>Password: {{ user.password }}</p>
          </div>
          <div class="img">
            <img :src="user.image" alt="image">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from "vue";

const users = ref([]);
const searchTerm = ref("");

onMounted(() => {
  fetch("https://dummyjson.com/users")
    .then((res) => res.json())
    .then((usr) => {
      users.value = usr.users;
    });
});

const filteredKitties = computed(() => {
  const regex = new RegExp(searchTerm.value, "gi");
  if (!searchTerm.value) {
    return users.value;
  } else {
    return users.value.filter((user) => {
      return (
        user.firstName.match(regex) ||
        user.lastName.match(regex) ||
        user.email.match(regex)
      );
    });
  }
});
</script>

<style scoped>
.users {
  display: flex;
  gap: 3rem;
  flex-direction: column;
  padding: 2rem;
}

.users input {
  width: 200px;
  margin: auto;
  padding: 0.7rem;
  border-radius: 10px;
  outline: none;
  border: none;
  box-shadow: 1px 2px 15px rgba(0, 0, 0, 0.4);
}
.wrapperDiv {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 15px;
  flex-wrap: wrap;
}
.user {
  box-shadow: 1px 2px 14px rgba(0, 0, 0, 0.1);
  padding: 1rem;
  width: calc(33% - 30px);
  border-radius: 14px;
}
.userInfo {
  flex: 65%;
}
.userInfo > p > span {
  font-size: 1.4rem;
  color: rgb(158, 150, 66);
}
.singleUser {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.img {
  flex: 35%;
  text-align: end;
}
.singleUser .img img {
  width: 89px;
}

@media (max-width: 1200px) {
  .user {
    width: calc(50% - 15px);
  }
}
@media (max-width: 768px) {
  .user {
    width: 100%;
  }
}
</style>
