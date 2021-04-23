<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Working with external libraries in Vue - Bootstrap</h2>
    <button type="button" class="btn btn-primary">Primary</button>
    <button type="button" class="btn btn-secondary">Secondary</button>
    <button type="button" class="btn btn-success">Success</button>
    <button type="button" class="btn btn-danger">Danger</button>
    <button type="button" class="btn btn-warning">Warning</button>
    <button type="button" class="btn btn-info">Info</button>
    <button type="button" class="btn btn-light">Light</button>
    <button type="button" class="btn btn-dark">Dark</button>
    <button type="button" class="btn btn-link">Link</button>

    <div class="alert alert-warning altert-dismissible fade show" role="alert">
      <strong>Hi!</strong> I'm Micheal
      <button type="button" class="close" data-dismiss="alert" aria-label="Close">
        <span aria-hidden="true">x</span>
      </button>
    </div>


    <!-- bootstrap-vue -->
      <div>
      <b-alert show>Default Alert</b-alert>

      <b-alert variant="success" show>Success Alert</b-alert>

      <b-alert v-model="showDismissibleAlert" variant="danger" dismissible>
        Dismissible Alert!
      </b-alert>

      <b-alert
        :show="dismissCountDown"
        dismissible
        variant="warning"
        @dismissed="dismissCountDown=0"
        @dismiss-count-down="countDownChanged"
      >
        <p>This alert will dismiss after {{ dismissCountDown }} seconds...</p>
        <b-progress
          variant="warning"
          :max="dismissSecs"
          :value="dismissCountDown"
          height="4px"
        ></b-progress>
      </b-alert>

      <b-button @click="showAlert" variant="info" class="m-1">
        Show alert with count-down timer
      </b-button>
      <b-button @click="showDismissibleAlert=true" variant="info" class="m-1">
        Show dismissible alert ({{ showDismissibleAlert ? 'visible' : 'hidden' }})
      </b-button>
    </div>

    <div>
      <b-alert show variant="primary">Primary Alert</b-alert>
      <b-alert show variant="secondary">Secondary Alert</b-alert>
      <b-alert show variant="success">Success Alert</b-alert>
      <b-alert show variant="danger">Danger Alert</b-alert>
      <b-alert show variant="warning">Warning Alert</b-alert>
      <b-alert show variant="info">Info Alert</b-alert>
      <b-alert show variant="light">Light Alert</b-alert>
      <b-alert show variant="dark">Dark Alert</b-alert>
    </div>

    <!-- splide library -->
    <div>
      <carousel>
        <slide>
          <img src="../assets/cat.jpeg" alt="cat" class="animal">
        </slide>
        <slide>
          <img src="../assets/rabbit.jpeg" alt="rabbit" class="animal">
        </slide>
        <slide>
          <img src="../assets/dog.jpeg" alt="dog" class="animal">
        </slide>
        <slide>
          <img src="../assets/puppy.jpeg" alt="puppy" class="animal">
        </slide>
      </carousel>
    </div>
    
    <!-- Vueper slides -->
    <div>
      <vueper-slides>
        <vueper-slide v-for="(slide, i) in slides" :key="i" :title="slide.title" :content="slide.content" />
      </vueper-slides>
    </div>
  </div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel';
import { VueperSlides, VueperSlide } from 'vueperslides'
import 'vueperslides/dist/vueperslides.css'

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components: {
    Carousel,
    Slide,
    VueperSlides,
    VueperSlide
  },
  data() {
      return {
        dismissSecs: 10,
        dismissCountDown: 0,
        showDismissibleAlert: false,
        options: {
          rewind: true,
          width: 800,
          perPage: 1,
          gap: '1rem',
        },
        slides: [
          {
            title: 'Slide #1',
            content: 'Slide content.'
          },
          {
            title: 'Slide #2',
            content: 'Slide content.'
          },
          {
            title: 'Slide #3',
            content: 'Slide content.'
          },
          {
            title: 'Slide #4',
            content: 'Slide content.'
          }
        ]
      }
    },
    methods: {
      countDownChanged(dismissCountDown) {
        this.dismissCountDown = dismissCountDown
      },
      showAlert() {
        this.dismissCountDown = this.dismissSecs
      }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.animal {
  height: 500px;
}
</style>
