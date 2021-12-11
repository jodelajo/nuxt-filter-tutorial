<template>
  <div class="container">
    <div class="dropdown-wrapper">
      <div @click="isVisible = !isVisible" class="selected-item">
        <span>{{ selectedItem.name }}</span>
        <svg
          class="dropdown-icon"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
          width="24"
          height="24"
        >
          <path fill="none" d="M0 0h24v24H0z" />
          <path
            d="M12 10.828l-4.95 4.95-1.414-1.414L12 8l6.364 6.364-1.414 1.414z"
          />
        </svg>
      </div>
      <div v-if="isVisible" class="dropdown-popover">
        <input
          v-model="searchQuery"
          type="text"
          placeholder="Search for User"
        />
        <div class="options">
          <ul class="list">
            <li
              @click="selectItem(user)"
              v-for="(user, index) in filteredUser"
              :key="`user-${index}`"
            >
              {{ user.name }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
      selectedItem: null,
      isVisible: false,
      userArray: [],
    };
  },
  computed: {
    filteredUser() {
      const query = this.searchQuery.toLowerCase();
      if (this.searchQuery === "") {
        return this.userArray;
      }
      return this.userArray.filter((user) => {
        return Object.values(user).some((word) =>
          String(word).toLowerCase().includes(query)
        );
      });
    },
  },
  methods: {
    selectItem(user) {
      this.selectedItem = user.name;
    },
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((res) => res.json())
      .then((json) => {
        console.log(json);
        this.userArray = json;
      });
  },
};
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
  font-size: 18px;
  font-weight: 700;
}

.dropdown-popover {
  position: absolute;
  border: 2px solid lightgray;
  top: 46px;
  left: 0;
  right: 0;
  background-color: white;
  max-width: 100%;
  padding: 10px;
}
input {
  width: 90%;
  height: 30px;
  border: 2px solid lightgray;
  font-size: 16px;
  padding-left: 8px;
}
.options {
  width: 100%;
  overflow-y: scroll;
  max-height: 200px;
}
.list {
  list-style: none;
  text-align: left;
  padding-left: 8px;
  max-height: 180px;
}
.options li {
  width: 100%;
  border-bottom: 1px solid lightgray;
  padding: 10px;
  background-color: #f1f1f1;
  cursor: pointer;
  font-size: 16px;
}
.options li:hover {
  background-color: #70878a;
  color: white;
  font-weight: bold;
}
</style>
