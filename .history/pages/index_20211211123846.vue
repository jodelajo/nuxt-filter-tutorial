<template>
  <div class="container">
    <div class="dropdown-wrapper">
      <div class="selected-item">
        <span>Select User</span>
      </div>
      <div class="dropdown-popover">
        <input
          v-model="searchQuery"
          type="text"
          placeholder="Search for User"
        />
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
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@100;200;300;500;700;900&family=Readex+Pro:wght@300;500;700&display=swap");

body {
  width: 100vw;
  height: 100vh;
}
.container {
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
  align-items: center;
  justify-content: center;
   font-family: "Montserrat", sans-serif;
   font-weight: 300;
   font-size: 16px;
   
}
.dropdown-wrapper {
  width: 350px;
  height: auto;
  /* max-width: 350px; */
  position: relative;
  display: flex;
  text-align: center;
  justify-content: center;
  margin: 0 auto;
}
.selected-item {
  height: 40px;
  width: 100%;
  border: 2px solid lightgray;
  border-radius: 5px;
  padding: 5px 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 20px;
  font-weight: 500;
}

.dropdown-popover{
  position: absolute;
  border: 2px solid lightgray;
  top: 46px;
  left: 0;
  right: 0;
  background-color: white;
  width: 100%;

}
input {
  width: 90%;
  height: 30px;
  border: 2px solid lightgray;
}
</style>
