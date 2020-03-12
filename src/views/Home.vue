<template>
  <div class="wrapper">
    <div class="background-text"><h1>DESIGNER</h1></div>
    <div class="about-spinning">
      <router-link to="/about"
        ><img src="../assets/about.png" alt="about"
      /></router-link>
    </div>
    <div class="container">
      <div class="profession">
        <ul>
          <li v-for="profession in professions" :key="profession.id">
            {{ profession.name }}
          </li>
        </ul>

        <p>
          Want to work with me? Do not hesitate to
          <span><router-link to="/contact">contact</router-link></span> me!
        </p>
      </div>
      <h2 class="home-title">
        <span>Hello<span class="circle">.</span></span>
        <span>I am</span>
        <span>Bodhi</span>
      </h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data: function() {
    return {
      professions: [
        {
          id: 1,
          name: "Web developer"
        },
        {
          id: 2,
          name: "Web designer"
        },
        {
          id: 3,
          name: "Freelancer"
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
.about-spinning {
  width: 180px;
  height: 180px;
  position: absolute;
  right: 880px;
  top: 250px;
  cursor: pointer;
  transform: skewX(30deg);

  transition: 0.5s ease-in-out;

  img {
    width: 100%;
    animation: spin 7s infinite linear;

    height: 100%;
  }

  @keyframes spin {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }
}
.background-text {
  position: absolute;
  font-size: 10rem;
  z-index: -8;
  top: 25vh;
  right: 4vw;

  color: rgba(255, 255, 255, 0.02);
  transform: rotate(14deg) skewX(-30deg);
}

.profession {
  color: white;
  width: 300px;
  ul {
    transform: rotate(-90deg) translateX(-500px);
    display: flex;
    justify-content: space-between;

    position: absolute;
    left: -100px;
    width: 400px;

    li {
      margin-bottom: 10px;
      position: relative;
    }
  }

  p {
    padding-top: 3.3rem;
    padding-left: 1rem;
    font-size: 1.7rem;
    span {
      position: relative;
      padding: 0 5px;

      &::before {
        content: "";
        position: absolute;
        height: 2px;
        background: white;
        bottom: 0;
        width: 93%;

        transition: 0.3s ease-in-out;
      }

      &:hover::before {
        width: 0;
      }

      &::after {
        position: absolute;
        pointer-events: none;
        content: "";
        transition: 0.3s ease-in-out;

        display: block;
        height: 100%;
        width: 0px;
        left: 0;
        top: 0;
        background: rgba(255, 0, 0, 0.233);
      }

      &:hover::after {
        width: 100%;
      }
    }
  }
}
.home-title {
  display: flex;
  flex-direction: column;
  padding-top: 1.2rem;

  font-size: 13rem;
  color: white;
  pointer-events: none;
}

@media screen and (max-width: 1700px) {
  .background-text {
    right: 0;
  }
}

.about-spinning {
  right: 45vw;
}

@media screen and (max-width: 1600px) {
  .background-text {
    font-size: 9rem;
  }
}

@media screen and (max-width: 1400px) {
  .background-text {
    top: 35vh;
    left: 4vw;
    font-size: 7rem;
  }

  .about-spinning {
    left: 35vw;
  }
}

@media screen and (max-width: 1100px) {
  .background-text {
    font-size: 6rem;
  }

  .home-title {
    font-size: 10rem;

    padding-top: 10vh;
  }

  .about-spinning {
    width: 140px;
    height: 140px;

    top: 32vh;
    left: 40vw;
  }
}

@media screen and (max-width: 850px) {
  .container {
    grid-template-rows: 1fr 240px;
    grid-template-columns: 1fr;
    grid-template-areas:
      "title"
      "text";
  }
  .home-title {
    font-size: 10rem;
    padding-top: 4rem;
    padding-right: 10vw;
    grid-area: title;
  }

  .profession {
    grid-area: text;
    p {
      top: 4vh;
      position: relative;
      left: 40vw;
      font-size: 1.4rem;
    }

    ul {
      transform: rotate(0) translateX(0);

      left: 11vw;
      bottom: 20vh;
    }
  }

  .about-spinning {
    width: 100px;
    height: 100px;

    top: 27vh;
    left: 63vw;
  }
}

@media screen and (max-width: 640px) {
  .home-title {
    padding-top: 3rem;
    font-size: 8rem;
  }
  .about-spinning {
    left: 60vw;
    top: 25vh;
  }

  .profession {
    p {
      top: 6vh;
      left: 37vw;
      font-size: 1.2rem;
    }
  }
}

@media screen and (max-width: 420px) {
  .about-spinning {
    top: 88vh;
    left: 48vw;

    height: 140px;
    width: 140px;

    transform: skewX(-30deg);
  }

  .profession {
    p {
      font-size: 1.6rem;
      left: 0;
      top: 10vh;

      padding-top: 7rem;
      padding-bottom: 3rem;
    }
  }
}

@media screen and (max-width: 375px) {
  .about-spinning {
    top: 79vh;
  }
}
</style>
