<template>
  <div class="container">
    <h1 class="background-text">WORK</h1>

    <h1>
      Work with <span>me<span class="circle">.</span></span>
    </h1>

    <div class="work-text">
      <h2>Do you want work with me? Turn your wildest designs into code?</h2>

      <p>
        Look no more. You are at the right address. Get in
        <span><router-link to="/contact">touch</router-link></span> with me and
        we can get started!
      </p>

      <div class="projects">
        <h3>Projects</h3>

        <div class="prev">
          <img
            src="../assets/prev.svg"
            alt="arrow previous"
            class="arrow prev"
            @click="prevImage"
          />
        </div>

        <div class="next">
          <img
            src="../assets/next.svg"
            alt="arrow next"
            class="arrow next"
            @click="nextImage"
          />
        </div>

        <div class="project-wrapper">
          <div
            v-for="projectImage in projectImages"
            :key="projectImage.id"
            class="img-wrapper"
          >
            <img :src="projectImage.src" alt="" />
          </div>
        </div>
      </div>
      <p>Not so much, but it's coming together!</p>

      <img src="../assets/work.jpg" alt="it ain't much but it's honest work" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Work",
  data() {
    return {
      projectImages: [
        {
          id: 1,
          src: require("../assets/rooms.png")
        },
        {
          id: 2,
          src: require("../assets/menu_rooms.png")
        },
        {
          id: 3,
          src: require("../assets/unknown.png")
        },
        {
          id: 4,
          src: require("../assets/dionysos.png")
        },
        {
          id: 5,
          src: require("../assets/dionysos_how.png")
        }
      ],
      counter: 0
    };
  },
  methods: {
    nextImage() {
      const wrapper = document.querySelector(".project-wrapper");

      if (this.counter >= 0 && this.counter < this.projectImages.length - 1) {
        this.counter++;
        wrapper.style.transform = `translateX(-${this.counter}00%)`;
      }
    },
    prevImage() {
      const wrapper = document.querySelector(".project-wrapper");

      if (this.counter !== 0) {
        this.counter--;

        wrapper.style.transform = `translateX(-${this.counter}00%)`;
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.background-text {
  position: fixed;

  top: 200px;
  transform: rotate(14deg) skewX(-30deg);

  z-index: -8;
  font-size: 20rem;
  color: rgba(255, 255, 255, 0.02);
}

h1 {
  color: white;
  font-size: 12rem;

  span {
    position: relative;
  }
}

.work-text {
  padding-top: 2.1rem;
  padding-right: 4rem;
  color: white;
  padding-left: 2rem;

  p {
    margin-top: 24px;
    font-size: 1.2rem;

    span {
      position: relative;
      padding: 4px 3px 0 3px;

      &::after {
        position: absolute;
        z-index: -1;
        left: 0;
        bottom: 0;
        content: "";

        height: 8px;
        width: 100%;
        background: rgba(32, 0, 211, 0.623);

        transition: 0.4s ease-out;
      }
    }
  }

  img {
    margin: 24px 0;
    width: 600px;
  }

  .projects {
    height: 400px;
    width: 550px;
    overflow: hidden;
    padding-top: 2.5rem;
    position: relative;

    h3 {
      padding-bottom: 2rem;
    }

    .arrow {
      position: absolute;
      width: 40px;
      cursor: pointer;
      top: 50%;
      transform: translateY(-50%);
      z-index: 5;
    }
    .prev {
      left: -10px;
    }

    .next {
      right: 0;
    }

    .project-wrapper {
      width: 100%;
      position: relative;
      // left: -30px;
      height: 100%;

      transition: 0.9s cubic-bezier(0.68, -0.55, 0.265, 1.55);

      .img-wrapper {
        width: 800px;
        position: absolute;

        &:nth-of-type(2) {
          left: 100%;
        }

        &:nth-of-type(3) {
          left: 200%;
        }
        &:nth-of-type(4) {
          left: 300%;
        }

        &:nth-of-type(5) {
          left: 400%;
        }
        img {
          padding-left: 40px;

          width: 100%;
          max-width: 500px;
        }
      }
    }
  }
}

// NOG RESPONSIVE MAKEN!!

@media screen and (max-width: 1024px) {
  .work-text {
    transform: translate(0, 50px);
  }
}

@media screen and (max-width: 800px) {
  .container {
    grid-template-rows: 1fr 240px;
    grid-template-columns: 1fr;
    grid-template-areas:
      "title"
      "text";

    h1 {
      font-size: 8rem;
    }
  }

  .work-text {
    width: 100%;

    .projects {
      width: 300px;
      height: 300px;

      .arrow {
        width: 20px;
        top: 85%;
      }

      .prev {
        left: 0;
      }

      .next {
        right: 10%;
      }

      .project-wrapper {
        left: -30px;
        .img-wrapper {
          width: 300px;
        }
      }
    }

    img {
      width: 300px;
    }
  }
}
</style>
