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
      <ul class="desk-list">
        <li><router-link to="/about">About</router-link></li>
        <li><router-link to="/work-with-me">Work with me</router-link></li>
        <li><router-link to="/contact">Contact</router-link></li>
      </ul>

      <div class="burger-menu" @click="openNav">
        <div class="burger-menu-line"></div>
        <div class="burger-menu-line"></div>
        <div class="burger-menu-line"></div>
      </div>

      <div class="burger-wrapper">
        <ul class="burger-list">
          <li @click="closeNav">
            <router-link to="/about">About</router-link>
          </li>
          <li @click="closeNav">
            <router-link to="/work-with-me">Work with me</router-link>
          </li>
          <li @click="closeNav">
            <router-link to="/contact">Contact</router-link>
          </li>
        </ul>
      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
import customCursor from "./components/Cursor.vue";

export default {
  data: function() {
    return {
      logo: "<bowdy />",
      navOpen: false
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
    },
    openNav: function() {
      const burgerWrapper = document.querySelector(".burger-wrapper");

      if (!this.navOpen) {
        burgerWrapper.style.opacity = "1";
        burgerWrapper.style.pointerEvents = "all";

        this.navOpen = true;
      } else if (this.navOpen) {
        burgerWrapper.style.opacity = "0";
        burgerWrapper.style.pointerEvents = "none";

        this.navOpen = false;
      }
    },
    closeNav: function() {
      const burgerWrapper = document.querySelector(".burger-wrapper");

      burgerWrapper.style.opacity = "0";
      burgerWrapper.style.pointerEvents = "none";
      this.navOpen = false;
    }
  },
  mounted() {
    document.addEventListener("click", this.setColor);
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700;800;900&display=swap");

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
  width: 100vw !important;
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

      z-index: 10;
    }

    .desk-list {
      margin-right: 100px;
      display: flex;
      width: 400px;
      justify-content: space-between;
    }

    .burger-menu {
      position: absolute;
      right: 0;

      display: none;
      width: 40px;
      height: 20px;
      margin-top: 4px;

      z-index: 5;
      cursor: pointer;

      transition: 0.2s ease-in-out;

      &-line {
        width: 100%;
        height: 2px;
        cursor: pointer;

        background: white;
        &:nth-of-type(2) {
          transform: translateY(5px);
          width: 50%;
        }

        &:nth-of-type(3) {
          transform: translateY(10px);
          width: 70%;
        }
      }
    }

    .burger-wrapper {
      display: none;
      background: rgba(0, 0, 0, 0.808);

      height: 100%;
      width: 100%;
      padding: 30px 0;
      position: absolute;
      right: 0;
      top: 0;
      z-index: 4;

      overflow: hiddden;

      transition: 0.5s cubic-bezier(0.47, 0, 0.745, 0.715);

      opacity: 0;

      .burger-list {
        display: none;
      }
    }
  }
}

@media screen and(max-width: 1580px) {
  .title-about {
    h1 {
      font-size: 11rem;
    }
  }
}

@media screen and (max-width: 1024px) and (max-height: 1366px) {
  * {
    cursor: auto;
  }

  .custom-cursor {
    display: none;
  }
}

@media screen and (max-width: 1000px) {
  #app {
    #nav {
      .desk-list {
        display: none;
      }

      .burger-menu {
        display: inline-block;
      }

      .burger-wrapper {
        overflow: hidden;
        display: inline-block;

        width: 100%;
        height: 800px;
        .burger-list {
          display: flex;
          flex-direction: column;
          width: 100%;
          height: 100%;

          justify-content: space-between;
          align-items: center;

          font-size: 2rem;
          padding: 80px 0;
        }
      }
    }
  }

  .title-about {
    h1 {
      font-size: 9rem;
    }
  }
}

@media screen and (max-width: 500px) {
  #app {
    #nav {
      .burger-menu {
        margin-right: 0;
      }
    }
  }
}

@media screen and (max-width: 425px) {
  #app {
    #nav {
      .home {
        margin: 50px;
      }
      .burger-menu {
        margin-right: -40px;
      }

      .burger-wrapper {
        right: -100px;
      }
    }
  }
  .title-about {
    h1 {
      font-size: 7rem;

      margin-top: 1rem;
    }
  }
}
</style>
