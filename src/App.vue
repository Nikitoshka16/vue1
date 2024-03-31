<template>
  <info-form
    :infoVisible = 'infoVisible'
    @isVisible = 'isVisible'
    @isInvisible = 'isInvisible'
  >
  </info-form>

  <facts-form
    :fact = 'fact'
    @getFact = 'getFact'
  >

  </facts-form>
</template>

<script>
import FactsForm from './components/FactsForm.vue'
import InfoForm from './components/InfoForm.vue'
import axios from "axios";


export default {
  name: 'App',
  components: {
    InfoForm,
    FactsForm
  },
  data() {
    return {
      fact: '',
      infoVisible: false
    }
  },
  methods: {
    isVisible() {
      this.infoVisible = true;
    },
    isInvisible() {
      this.infoVisible = false;
    },
    async getFact() {
      try {
        const res = await axios.get('https://catfact.ninja/fact');
        console.log(res);
        this.fact = res.data.fact;
        this.translate(this.fact);
      }catch(e){
        console.log(e); 
        if(e.name == "AxiosError") {
          this.fact = "Ошибка получения данных, проверьте подключение к интернету!";
        }
      }
    },
    async translate(fact) {
      axios.post("https://translate.googleapis.com/translate_a/single?format=text&client=gtx&sl=en&tl=ru&dt=t&q=" + fact)
        .then(res => {
          // console.log(res.data[0][0][0]);
          this.fact = res.data[0][0][0];
          
        })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5em;
}
button {
  border: 0.1em teal solid;
  border-radius: 3em;
  padding: 0.5em;
}
</style>
