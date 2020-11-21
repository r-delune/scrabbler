<template>
  <v-container align-center fluid fill-height>
    <v-row align-center justify="center">
      <v-col lg="auto">
    <v-row align-center justify="center">
<span class="icon mdi mdi-skateboard"></span>

       </v-row >  
      <!-- <logo /> -->
      <h2 >
        Seans Scrabbler
      </h2>
 
      <h5 v-if="content" >There are {{ content.words.length }} words to go through</h5>
 </v-col>
    </v-row >  

    
    <v-row align-center justify="center">
                      <!-- email -->
                <v-text-field
                  v-model="word_display"
                  label=""
              
                  name="task"
                   class="mx-5"
                  disabled
                >
                </v-text-field>

                 <v-text-field
                  v-model="guess"
               
                  label="Enter Guess"
                  name="guess"
                  class="mx-5"
                  required
                >
                </v-text-field>


              </v-row >  

          <v-row align-center justify="center">
              <v-col cols='6'>
                 <v-btn large  @click="scrabble()"> New Word </v-btn>
              </v-col>  
              <v-col cols='6'>
                 <v-btn large @click="guess_answer()"> Check! </v-btn>
              </v-col>
            
              </v-row >     

  </v-container>
</template>

<script>
import Logo from '~/components/Logo.vue'

import content from '../assets/content/scrabble_words.json'
export default {
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },
  components: {
    Logo
  },
    data() {
    return {
      guess: '',
      word_display: '',
      answer: '',
    }},
  computed: {
    content () {
      return this.$store.state.home.data
    },
  },
  mounted() {
    this.scrabble()
  },
  methods:{
     scrabble () {
       console.log('scrabbling..',this.content.words)

          console.log('length is..', this.content.words.length)
          // choose random element
          this.answer  = this.content.words[Math.floor(Math.random() * this.content.words.length)];


          this.word_display =  this.answer.split('').sort().join('');

 console.log('jumbled is is..', this.word_display)

  console.log('answer is is..', this.answer)
     },
          guess_answer () {
       console.log('guessing..', this.guess)
        console.log('answer..', this.answer)

        if (this.guess === this.answer) {
          console.log('this answer is correcnt..')
          this.word_display = 'Correct!!! The answer is ' + this.answer + ''
        }else{
           this.word_display = 'Wrong!!! The answer is ' + this.answer+ ''
        }
     }
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  background-color: green;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.icon{
 
    width: 100%;
        font-size: 137px;
    color: var(--primary-text-color);
}

</style>
