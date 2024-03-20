<template>
    <nav :class="[darkTheme ? 'isActive' : '']">
      <img :src="logo" alt="">
      <ul>
        <li v-for="(page, idx) in pagesData" :key="idx">
          <a 
          :class="[darkTheme ? 'isActive' : '']"
          :href="page.url">{{page.name}}</a>
        </li>
      </ul>
      <button 
      :class="[darkTheme ? 'isActive' : '']"
      @click.prevent="darkTheme = !darkTheme">Change theme</button>
    </nav>
</template>

<script>
import pagesData from '@/data/pagesData';
import logo from '@/assets/arLogo.png';


export default {
  data() {
    return {
      pagesData: pagesData,
      logo: logo,
      darkTheme: false
    }
  }
}
</script>


//CSS
<style scoped>
nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #E3E3E3;
    box-shadow: 1px 2px 8px rgba(0, 0, 0, 0.4);
    padding: 15px;
    transition: .2s linear;
}
nav img {
    width: 100px;
}
nav ul {
    display: flex;
}

nav ul li {
    list-style: none;
    margin-right: 15px;
}

nav ul li a {
    font-size: 1.4rem;
    transition: .2s linear;
    cursor: pointer;
    text-decoration: none;
    color: #4F8782;
}
nav ul li a:hover {
   color: orange;
}

nav ul li a.isActive {
  color: #fff;
}

button {
  padding: 0.8rem;
  background: #4F8782;
  color: #fff;
  border-radius: 8px;
  outline: none;
  border: 2px solid #4F8782;
  transition: .2s linear;
  letter-spacing: 1.2px;
  font-size: 1rem;
}

button:hover {
  background: transparent;
  color: #4F8782;
  cursor: pointer;
  transition: .2s linear;
}

button.isActive {
  background: #fff;
  color: #4F8782;
  border: 2px solid #fff;
}

nav.isActive {
  background: #4F8782;
  color: white;
  border-bottom: 2px solid rgba(0, 0, 0, 0.2);
}

.lightButton:hover {
  color: #fff;
}
</style>
