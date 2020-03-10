<template>
  <div id="app">
    <custom-cursor
      :targets="['a', 'arrow']"
      :circleColor="'rgb(255, 60, 60)'"
      :circleColorHover="'rgb(255, 16, 16)'"
      :dotColor="'rgba(255, 0, 55, 0.493)'"
      :dotColorHover="'rgba(255, 0, 55, 0.664)'"
      :hoverSize="1.4"
    />
    <div id="nav">
      <div class="home">
        <router-link to="/">{{ logo }}</router-link>
      </div>
      <ul>
        <li><router-link to="/about">About</router-link></li>
        <li><router-link to="/work-with-me">Work with me</router-link></li>
        <li><router-link to="/contact">Contact</router-link></li>
      </ul>
    </div>
    <router-view />
  </div>
</template>

<script>
import customCursor from "./components/Cursor.vue";

export default {
  data: function() {
    return {
      logo: "<bowdy />"
    };
  },
  components: {
    customCursor
  },
  methods: {
    setColor: function() {
      const circle = document.querySelector(".circle");
      const randomColor = Math.floor(Math.random() * 16777215).toString(16);

      circle.style.color = "#" + randomColor;
    }
  },
  mounted() {
    document.addEventListener("click", this.setColor);
  }
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;

  font-family: Montserrat;
  cursor: none;
}

body {
  background: rgb(30, 30, 30);
  position: relative;

  overflow-x: hidden;
}

ul {
  list-style-type: none;
}

a {
  text-decoration: none;
  color: white;
}

.cursor {
  position: absolute;

  height: 20px;
  width: 20px;
  border-radius: 50%;
  border: 1px solid rgb(255, 16, 16);

  background: rgba(255, 0, 55, 0.664);
}

.container {
  width: 80%;
  margin: 0 auto;

  display: grid;
  grid-template-columns: 1fr 1fr;
}

.title-about {
  h1 {
    color: white;
    position: relative;
    font-size: 13rem;
  }
}

#app {
  #nav {
    width: 100%;
    height: 128px;

    display: flex;
    align-items: center;

    .home {
      flex: 1;
      margin-left: 100px;

      letter-spacing: 8px;
      font-size: 1.9rem;
    }

    ul {
      margin-right: 100px;
      display: flex;
      width: 400px;
      justify-content: space-between;
    }
  }
}
</style>
