<template>
  <div>
    <section data-id="first-section" class="section-container">
      <div class="container">
        <div class="title">
          <h1>GSAP Study</h1>
          <p>↓scroll!!</p>
        </div>
      </div>
    </section>
    <section data-id="second-section" class="section-container">
      <div class="container -center">
        <div class="inner">
          <div class="section-wrapper">
            <div class="title">
              <h2 class="text">Mikai's voice</h2>
              <div class="line"></div>
            </div>
            <div class="container">
              <div class="inner">
                <div class="box"></div>
                <div class="text -first">
                  <p data-id="number-first" class="number">01</p>
                  <p data-id="text-first">社会人になるまで<br>人生で一度も笑顔を作った事が無かった。</p>
                </div>
                <div class="text -second">
                  <p data-id="number-second" class="number">02</p>
                  <p data-id="text-second">コードもsexyに書くから。</p>
                </div>
                <div class="text -third">
                  <p data-id="number-third" class="number">03</p>
                  <p data-id="text-third">だって考えてみてくださいよ。<br>偏差値30の人が東大受かりますか？って話ですよ。</p>
                </div>
              </div>
              <div class="images">
                <div class="box -first">
                  <img data-id="image-first" class="img" src="@/assets/images/image2.jpg" alt="">
                </div>
                <div class="box -second">
                  <img data-id="image-second" class="img" src="@/assets/images/1.png" alt="">
                </div>
                <div class="box -third">
                  <img data-id="image-third" class="img" src="@/assets/images/image3.jpeg" alt="">
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import { TweenMax, TimelineMax } from 'gsap';
export default {
  mounted() {

    // create scene
    const controller = new ScrollMagic.Controller();
    const tl = new TimelineMax();
    new ScrollMagic.Scene({
      triggerElement: "[data-id='second-section']",
      duration: '200%',
      triggerHook: 0,
      makers: true
    })
      .setTween(tl)
      .setPin("[data-id='second-section']")
      .addTo(controller);

    // timeline
    tl
    .to("[data-id='number-first']", 2, {
      y: - 100,
      opacity: 0
    })
    .to("[data-id='text-first']", 2, {
      y: - 100,
      opacity: 0
    }, '-=1.8')
    .to("[data-id='image-first']", 2, {
      opacity: 0,
      scale: 1.2
    }, '-=1.8')
    .from("[data-id='number-second']", 2, {
      y: 100,
      opacity: 0
    }, '-=1')
    .from("[data-id='text-second']", 2, {
      y: 100,
      opacity: 0
    }, '-=1.8')
    .to("[data-id='text-second']", 2, {
      opacity: 1
    })
    .to("[data-id='number-second']", 2, {
      opacity: 1
    })
    .to("[data-id='number-second']", 2, {
      y: - 100,
      opacity: 0
    })
    .to("[data-id='text-second']", 2, {
      y: - 100,
      opacity: 0
    }, '-=1.8')
    .to("[data-id='image-second']", 2, {
      opacity: 0,
      scale: 1.2
    }, '-=1.8')
    .from("[data-id='number-third']", 2, {
      y: 100,
      opacity: 0
    }, '-=1')
    .from("[data-id='text-third']", 2, {
      y: 100,
      opacity: 0
    }, '-=1.8')
  }
}
</script>

<style lang="scss" scoped>
.section-container {
  > .container {
    width: 70%;
    height: 100vh;
    margin: auto;
    padding: 100px 0;
    font-family: 'Montserrat', sans-serif;
    color: #17223b;
  }

  > .container > .inner {
    box-sizing: border-box;
  }
}

.section-wrapper {
  > .title {
    font-size: 80px;
    margin-bottom: 80px;
    text-align: right;
    position: relative;
    display: inline-block;
  }

  > .title > .text {
    margin-left: 50px;
    color: transparent;
    letter-spacing: 8px;
    text-stroke: 1px #263859;
    -webkit-text-stroke: 1px #263859;
  }

  > .title > .line {
    position: absolute;
    z-index: -1;
    top: -10px;
    left: 0;
    width: 100px;
    height: 100px;
    background-color: rgba(#ff6768, 0.7);
  }

  > .container {
    width: 100%;
    height: 100%;
    display: flex;
  }

  > .container > .inner {
    position: relative;
    width: 60%;
  }

  > .container > .inner > .text {
    position: absolute;
    font-size: 24px;
  }

  > .container > .inner > .text > .number {
    font-size: 4rem;
    font-weight: bold;
    margin-bottom: 12px;
    letter-spacing: 4px;
    color: #6b778d;
  }

  > .container > .images {
    position: relative;
    width: 40%;
  }

  > .container > .images > .box {
    position: absolute;
    width: 100%;
    height: 400px;
    overflow: hidden;
  }

  > .container > .images > .box.-first {
    z-index: 3;
  }
  > .container > .images > .box.-second {
    z-index: 2;
  }
  > .container > .images > .box.-third {
    z-index: 1;
  }

  > .container > .images > .box > .img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>