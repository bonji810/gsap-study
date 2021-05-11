<template>
  <div class="body">
    <section class="section-container">
      <div class="container -center">
        <div class="main-container">
          <div class="container">
            <div class="title">
              <h1 class="text">
                <span class="span" data-id="main-title">G</span>
                <span class="span" data-id="main-title">S</span>
                <span class="span" data-id="main-title">A</span>
                <span class="span" data-id="main-title">P</span>
                <span class="span" data-id="main-title">-</span>
                <span class="span" data-id="main-title">S</span>
                <span class="span" data-id="main-title">t</span>
                <span class="span" data-id="main-title">u</span>
                <span class="span" data-id="main-title">d</span>
                <span class="span" data-id="main-title">y</span>
              </h1>
            </div>
            <div class="inner">
              <p>▼ click!</p>
              <div @click="boxClick" data-id="box" class="box"></div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section data-id="second-section" class="section-container">
      <div class="container">
        <div class="inner">
          <div class="card-container">
            <div class="container">
              <div class="inner">
                <p class="name">JUN MIKAI</p>
                <p class="subname">三海　純</p>
                <p class="text">
                  実際、1日15〜16時間勉強するって普通のことだと思ってたんですよ。<br>
                  寝ることと食べること以外の時間は1日頑張るっていうのは、
                  毎日歯磨きをすること同じくらいの感覚なんですよね。
                </p>
              </div>
              <div data-id="card-image" class="image">
                <img class="img" src="@/assets/images/1.png" alt="">
                <div data-id="card-box" class="box"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="section-container">
      <div class="container">

      </div>
    </section>
  </div>
</template>

<script>
import { gsap, Power4 } from 'gsap';
import { ScrollTrigger } from 'gsap/dist/ScrollTrigger'
gsap.registerPlugin(ScrollTrigger)

export default {
  mounted() {
    gsap.from("[data-id='main-title']", 1, {
      y: '120%',
      ease: Power4.easeOut,
      stagger: {
        from: 'random',
        amount: 0.4
      }
    })
    const timeline = gsap.timeline({
      scrollTrigger: {
        markers: true,
        trigger: "[data-id='second-section']",
        start: "top center",
        end: "bottom",
        toggleActions: "play pause resume reset"
      }
    })
    timeline.from("[data-id='card-image']", 0.8, {
      y: '30%',
      opacity: 0,
      ease: Power4.easeOut
    })
    .from("[data-id='card-box']", 0.8, {
      width: 0,
      ease: Power4.easeOut
    },'-=0.4')
  },
  methods: {
    boxClick() {
      console.log('circleclick!')
      const tl = gsap.timeline();
      tl.to("[data-id='box']", 1, {
        scale: 2,
        rotate: '360deg',
        ease: Power4.easeOut
      })
      .to("[data-id='box']", 1, {
        scale: 1,
        rotate: '-360deg',
        ease: Power4.easeOut
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.body {
  background-color: #515A8E;
}

.section-container {
  > .container {
    width: 80%;
    height: 100vh;
    padding: 100px 0;
    margin: auto;
    font-family: 'Montserrat', sans-serif;
    color: #EDD5BD;
  }

  > .container.-center {
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

.main-container {
  > .container > .title {
      text-align: center;
      overflow: hidden;
  }

  > .container > .title > .text {
      font-size: 6rem;
      margin-bottom: 32px;
  }

  > .container > .title > .text > .span {
    display: inline-block;
    letter-spacing: 0px;
  }

  > .container > .inner {
    text-align: center;
  }

  > .container > .inner > .box {
    width: 100px;
    height: 100px;
    margin: auto;
    background-color: #F789A4;
    cursor: pointer;
  }
}

.card-container {
  > .container {
    display: flex;
    justify-content: space-between;
  }

  > .container > .inner {
    width: 40%;
    margin-right: 40px;
  }

  > .container > .inner > .name {
    font-size: 4.4rem;
    margin-bottom: 18px;
    font-weight: bold;
  }
  > .container > .inner > .subname {
    font-size: 2rem;
    margin-bottom: 40px;
  }

  > .container > .image {
    position: relative;
    z-index: 2;
    width: 50%;
    height: 400px;
  }

  > .container > .image > .box {
    position: absolute;
    z-index: 1;
    top: 10%;
    left: 10%;
    width: 100%;
    height: 100%;
    background-color: #F789A4;
  }

  > .container > .image > .img {
    position: relative;
    z-index: 2;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}

</style>
