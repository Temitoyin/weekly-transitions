<script>
export default {
  data() {
    return {
      items: [{ message: "Flowers" }, { message: "Vases" }],
    };
  },
};
</script>

<template>
  <div class="navigation">
    <ul class="navigation__list">
      <li v-for="item in items">{{ item.message }}</li>
    </ul>
    <div class="navigation__logo">
      <h1 class="logo__header">La fleur</h1>
    </div>
    <div class="navigation__options"></div>
  </div>
</template>

<style scoped>
.navigation {
  position: fixed;
  display: flex;
  justify-content: space-between;
  border-bottom: 1px solid white;
  width: 100%;
  z-index: 1000;
  padding: 1rem;
  color: white;
}
.navigation__list {
  display: flex;
  font-family: "Roboto", sans-serif;
  width: 30%;
}
.navigation__logo {
  align-self: center;
}
.navigation__options {
  width: 30%;
}
.logo__header {
  font-size: 21px;
  font-family: ;
}
ul {
  list-style-type: none;
}
li {
  font-size: 18px;
  margin-right: 40px;
}
li:hover {
  color: maroon;
  cursor: pointer;
}
</style>
