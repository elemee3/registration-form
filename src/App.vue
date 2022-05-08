<script>
import Form from '@/components/Form.vue'

export default {
  components: {
    Form,
  },
}
</script>

<template>
  <header>
    <img alt="logo" class="logo" src="@/assets/logo.png" width="80" height="80" />

    <div class="menu-items">
      <a href="#" class="menu-item">Help</a>
      <a href="#" class="menu-item logo-blue">Save and Finish Later</a>
    </div>
  </header>

  <body>
    <Form />
  </body>

</template>

<style>
@import '@/assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  font-weight: normal;
}

header {
  display: flex;
  justify-content: space-evenly;
  background-color: white;
  padding: 10px;
}

.logo {
  align-items: flex-end;
  justify-content: flex-end;
}

.menu-items {
  display: flex;
  align-items: flex-end;
  margin-bottom: 10px;
}

.menu-item {
  margin: 5px;
}

.menu-item:hover {
  color: #00aeef;
}

.logo-blue {
  color: #00aeef;
}

.logo-blue:hover {
  color: black;
}

a {
  text-decoration: none;
  transition: 0.4s;
  color: black;
}

body {
  background-color: #f6f6f6;
}
</style>
