<template>
  <div class="container">
    <section class="dropdown-wrapper">
    <div class="selected-item">
      <span>Select User</span>
    </div>
    <div class="dropdown-popover">
      <input v-model="searchQuery" type="text" placeholder="Search for User">
      <div class="options">
        <ul>
          <li>Merlijn</li>
          <li>Charlie</li>
          <li>Sasha</li>
          <li>BiBi</li>
          <li>Jodelajo</li>
        </ul>
      </div>
    </div>
  </section>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style  scoped>
.container {
  width: 100vw;
  height: 100vh;
}
.dropdown-wrapper {
  max-width: 350px;
  position: relative;
  display: flex;
}
.selected-item {
  height: 40px;
  border: 2px solid lightgray;
  border-radius: 5px;
  padding: 5px 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>