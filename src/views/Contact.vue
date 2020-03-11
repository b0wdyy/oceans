/* eslint-disable no-unused-labels */
<template>
  <div class="container">
    <div class="background-text">CONTACT</div>
    <div class="title-about">
      <h1>
        Contact <span>me<span class="circle">.</span></span>
      </h1>
    </div>

    <div class="text">
      <div v-for="icon in icons" :key="icon.id" class="grid-text">
        <img :src="icon.src" :alt="icon.alt" />

        <div>
          <h3>{{ icon.title }}</h3>
          <p v-html="icon.subtitle"></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Contact",
  data() {
    return {
      icons: [
        {
          id: 1,
          src: require("../assets/location.svg"),
          title: "Address",
          subtitle: "Based in Belgium. More specific Lommel, Limburg.",
          alt: "location"
        },
        {
          id: 2,
          src: require("../assets/phone.svg"),
          title: "Let's talk",
          subtitle: "<a href='tel:+324 88 08 94 42'>+324 88 08 94 42</a>",
          alt: "phone"
        },
        {
          id: 3,
          src: require("../assets/mail.svg"),
          title: "Or just mail me! (It's easier than calling)",
          subtitle:
            "<a href = 'mailto: vandaelbodhi@hotmail.com'>vandaelbodhi@hotmail.com</a>",
          alt: "mail"
        }
      ]
    };
  }
};
</script>

<style lang="scss">
.background-text {
  position: absolute;
  top: 40%;
  right: 10%;
  transform: rotate(14deg) skewX(-30deg);

  z-index: -8;
  font-size: 20rem;
  font-weight: 700;
  color: rgba(255, 255, 255, 0.02);
}

.text {
  position: absolute;
  top: 30vh;
  right: 7vw;

  .grid-text {
    color: white;

    display: flex;
    margin-left: 2rem;

    img {
      width: 30px;
      margin-right: 50px;

      transform: translateY(0.7vh);
    }

    div {
      h3 {
        margin-bottom: 2rem;
        margin-top: 4rem;
        font-size: 1.7rem;
      }

      a {
        position: relative;

        &::before {
          position: absolute;
          bottom: 0;
          right: 0;
          z-index: -5;
          content: "";

          width: 60%;
          height: 9px;

          background-color: rgba(220, 20, 60, 0.479);
        }
      }
    }
  }
}

@media screen and(max-width: 1700px) {
  .background-text {
    right: 3vw;
  }

  .text {
    right: 2vw;
  }
}
@media screen and (max-width: 1450px) {
  .background-text {
    font-size: 18rem;

    top: 30vh;
  }

  .text {
    top: 35vh;
  }
}

@media screen and (max-width: 1280px) {
  .background-text {
    font-size: 15rem;

    top: 35vh;
  }
}

@media screen and (max-width: 1150px) {
  .background-text {
    font-size: 14rem;

    top: 35vh;
  }

  .text {
    right: 8vw;
    top: 40vh;
    .grid-text {
      div {
        h3 {
          font-size: 1.2rem;
        }
      }
    }
  }
}

@media screen and (max-width: 1024px) and (max-height: 1366px) {
  .background-text {
    font-size: 12rem;
  }

  .text {
    right: 5vw;
    top: 36vh;

    width: 500px;

    .grid-text {
      img {
        transform: translateY(-0.9vh);
      }
      div {
        h3 {
          font-size: 2.5rem;
        }

        p {
          font-size: 1.5rem;
        }
      }
    }
  }
}

@media screen and (max-width: 1000px) {
  .background-text {
    font-size: 12rem;

    top: 35vh;
  }

  .text {
    right: 8vw;
    top: 40vh;
    .grid-text {
      div {
        h3 {
          font-size: 1rem;
        }
      }
    }
  }
}

@media screen and (max-width: 900px) {
  .background-text {
    font-size: 10.5rem;

    top: 35vh;
  }

  .text {
    right: 3vw;
    top: 37vh;
    .grid-text {
      div {
        h3 {
          font-size: 1.1rem;
        }

        p {
          font-size: 0.9rem;
        }
      }
    }
  }
}

@media screen and (max-width: 770px) {
  .background-text {
    display: none;
  }

  .text {
    right: 13vw;
    top: 50vh;
    .grid-text {
      div {
        width: 100%;
        h3 {
          font-size: 1.5rem;
        }

        p {
          font-size: 1.1rem;
        }
      }
    }
  }
}

@media screen and (max-width: 425px) {
  .text {
    left: 8vw;
    top: 55vh;

    width: 500px;
    padding-bottom: 2rem;
    .grid-text {
      img {
        transform: translateY(-0.6vh);
      }

      &:nth-of-type(1) {
        img {
          transform: translateY(-3vh);
        }
      }

      &:nth-of-type(3) {
        img {
          transform: translateY(-3.7vh);
        }
      }
      div {
        width: 400px;
        padding-bottom: 1.5rem;
        h3 {
          font-size: 2rem;
        }

        p {
          font-size: 1.3rem;
        }
      }
    }
  }
}

@media screen and (max-width: 375px) {
  .text {
    .grid-text {
      img {
        transform: translateY(-0.6vh);
      }

      &:nth-of-type(1) {
        img {
          transform: translateY(-2.8vh);
        }
      }

      &:nth-of-type(2) {
        img {
          transform: translateY(-1.2vh);
        }
      }

      &:nth-of-type(3) {
        img {
          transform: translateY(-3.3vh);
        }
      }
    }
  }
}

@media screen and (max-width: 360px) {
  .text {
    top: 60vh;
  }
}

@media screen and (max-width: 320px) {
  .text {
    top: 72vh;
  }
}
</style>
