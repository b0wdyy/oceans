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
  top: 200px;
  left: 0;
  transform: rotate(14deg) skewX(-30deg);

  z-index: -8;
  font-size: 20rem;
  font-weight: 700;
  color: rgba(255, 255, 255, 0.02);
}

.text {
  position: absolute;
  top: 35vh;
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
</style>
