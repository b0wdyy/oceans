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
  right: 780px;
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
  top: 200px;

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

  span:nth-of-type(1) {
    position: relative;
    width: 610px;
  }
}
</style>
