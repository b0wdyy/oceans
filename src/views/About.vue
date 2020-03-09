<template>
  <div class="container">
    <h1 class="background-text">ABOUT</h1>
    <div class="title-about">
      <h1>
        About <span>me<span class="circle">.</span></span>
      </h1>
    </div>

    <div class="about-text">
      <h3>Skills</h3>
      <ul class="skills">
        <li v-for="skill in skills" :key="skill.id">
          {{ skill.item }}
        </li>
      </ul>

      <div class="images">
        <ul>
          <li><img src="../assets/html-5.svg" alt="html 5" /></li>
          <li><img src="../assets/css.svg" alt="css" /></li>
          <li><img src="../assets/java-script.svg" alt="javascript" /></li>
          <li><img src="../assets/jquery.png" alt="jquery" /></li>
          <li><img src="../assets/php.svg" alt="php" /></li>
          <li>
            <img
              src="../assets/logo.png"
              alt="vueJS"
              style="filter:grayscale(1)"
            />
          </li>
          <li><img src="../assets/drupal.svg" alt="drupal" /></li>
        </ul>
      </div>

      <h3>Personal info</h3>
      <p>
        I am a 20 year old student from Lommel, Limburg. Currently studying
        front-end development. I love doing UI/UX work and of course making
        websites. The main languages I use are, HTML, CSS (SCSS), JavaScript,
        jQuery, PHP. I love reading books and I try to read 2 books each month.
      </p>
      <p>
        In my spare time I workout 5-6 times a week. Besides that I love
        spending time with friends and family.
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "About",
  data: function() {
    return {
      skills: [
        {
          id: 1,
          item: "HTML",
          img: "html-5.svg"
        },
        {
          id: 2,
          item: "CSS",
          img: "css.svg"
        },
        {
          id: 3,
          item: "JavaScript",
          img: "java-script.svg"
        },
        {
          id: 4,
          item: "jQuery",
          img: "jquery.png"
        },
        {
          id: 5,
          item: "PHP",
          img: "php.svg"
        },
        {
          id: 6,
          item: "VueJS",
          img: "logo.png"
        },
        {
          id: 7,
          item: "Drupal",
          img: ""
        }
      ]
    };
  },
  mounted() {
    window.onload(this.setColor);
  }
};
</script>

<style lang="scss" scoped>
.background-text {
  position: absolute;
  top: 200px;
  transform: rotate(14deg) skewX(-30deg);

  z-index: -8;
  font-size: 20rem;
  color: rgba(255, 255, 255, 0.02);
}

.title-about {
  h1 {
    color: white;
    position: relative;
    font-size: 13rem;

    span {
      position: relative;
      // span {
      //   color: rgb(107, 20, 220);
      // }
    }
  }
}

.about-text {
  padding-top: 3.6rem;
  margin-left: 3rem;
  transform: translateY(100px);
  overflow: hidden;

  h3 {
    color: white;
    padding-bottom: 32px;
  }

  .skills {
    position: relative;
    display: flex;
    justify-content: space-between;
    width: 600px;
    padding-bottom: 44px;

    animation: marquee 9s infinite linear;

    @keyframes marquee {
      from {
        transform: translateX(100%);
      }
      to {
        transform: translateX(-100%);
      }
    }

    li {
      color: white;
      margin-left: 10px;
    }
  }

  .images {
    margin-bottom: 30px;
    ul {
      display: flex;
      align-items: center;
      justify-content: space-between;
      background: white;
      padding: 10px 20px;

      img {
        max-width: 70px;
        width: 40px;

        &:nth-of-type(6) {
          filter: grayscale(1);
        }
      }
    }
  }

  p {
    font-size: 1.5rem;
    color: white;
    &:nth-of-type(1) {
      padding-bottom: 2rem;
    }
  }
}
</style>
