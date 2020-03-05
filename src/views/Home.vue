<template>
  <div class="wrapper">
    <div class="background-text"><h1>DESIGNER</h1></div>
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
        <span>Hello</span>
        <span>I am</span>
        <span>Bodh!</span>
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
.background-text {
  position: absolute;
  font-size: 10rem;
  z-index: -8;
  top: 200px;

  color: rgba(255, 255, 255, 0.02);
  transform: rotate(14deg) skewX(30deg);
}
.container {
  width: 80%;
  margin: 0 auto;

  display: grid;
  grid-template-columns: 1fr 1fr;

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

        &:nth-of-type(1) {
          left: 30px;
        }
        &:nth-of-type(2) {
          left: 20px;
        }
        &:nth-of-type(3) {
          left: 10px;
        }
      }
    }

    p {
      padding-top: 3.3rem;
      padding-left: 1rem;
      font-size: 1.7rem;
      span {
        position: relative;
        padding: 0 5px;

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

    span:nth-of-type(1) {
      position: relative;
      width: 610px;
      &::after {
        position: absolute;
        right: 0;
        bottom: 0;
        content: ".";
        display: block;
        color: crimson;
      }
    }
  }
}
</style>
