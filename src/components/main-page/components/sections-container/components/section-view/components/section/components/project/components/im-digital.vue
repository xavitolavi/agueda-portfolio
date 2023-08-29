<template>
  <div class="digital-project-container" v-if="selectedProject">
    <div class="video-wrapper">
      <iframe src="https://www.youtube.com/embed/-BtcUnrJ3Rw?si=hxIaNous5vsbCeUH&amp;controls=1&amp;autoplay=1" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
    </div>
      <div class="text">
        <span>I arrived at IM with the mission of redesigning the company's personal brand, which 
          had become outdated over the years. Our goal was to project a striking yet approachable 
          image while maintaining the essence of the corporate identity. To achieve this, I created 
          a wide variety of content, both graphic and multimedia, in order to promote the school, its 
          faculty, and educational offerings under a  renewed identity.</span>
      </div>
      <div class="im-digital-video-grid">
        <div class="video-wrapper">
          <iframe src="https://www.youtube.com/embed/-VYSSaoAyNc?si=VopB-qQ9AHl3Iu6A&amp;controls=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <div class="video-wrapper">
          <iframe src="https://www.youtube.com/embed/VFUZ5qK1lqM?si=sO-9nBtcAAdij8UZ&amp;controls=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>        <iframe src="https://www.youtube.com/embed/-BtcUnrJ3Rw?si=hxIaNous5vsbCeUH&amp;controls=2" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <div class="video-wrapper">
          <iframe src="https://www.youtube.com/embed/-MMBN19C2Uk?si=O6iL7aDs4ETl4r8u&amp;controls=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>        <iframe src="https://www.youtube.com/embed/-BtcUnrJ3Rw?si=hxIaNous5vsbCeUH&amp;controls=2" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <div class="video-wrapper">
          <iframe src="https://www.youtube.com/embed/89i3Jmurogo?si=pZ4z8QvIU71XfVBG&amp;controls=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <div class="video-wrapper">
          <iframe src="https://www.youtube.com/embed/w1DO-NjZwU0?si=zbh6Sp1E7gMMRDYS&amp;controls=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
        <div class="video-wrapper">
          <iframe src="https://www.youtube.com/embed/9_MvOEA5xIU?si=49UJieoQMCF14QR7&amp;controls=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
        </div>
      </div>
  </div>
</template>

<script>
  export default {
    name: 'ImDigitalProject',

    props: {
      selectedProject: {
          type: Object,
          default() {
              return {};
          }
      }
    },
  }
</script>

<style lang="less">
.digital-project-container {
    max-height: max-content;
    padding: 0 20rem;
    margin-bottom: 5rem;

    .video-wrapper {
      position: relative;
      padding-bottom: 56.25%;
      height: 0;
    }

    .video-wrapper iframe {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
    }

    .text {
      margin-top: 2rem;
      text-align: justify;
    }

    .im-digital-video-grid {
      margin-top: 2rem;
      display: grid;
      grid-template-columns: auto auto;
      grid-template-rows: auto;
      grid-gap: 2rem;
    }
}
</style>