<template>
  <div class="fact">
    <button
      @click="getFact"
    >
      Факт!
    </button>
    <h3>{{ fact }}</h3>
  </div>
</template>

<script>
export default {
    name: "FactsForm",
    props: {
      fact: String
    },
    data() {

    },
    methods: {
      getFact() {
        this.$emit('getFact');
      }
    }

}
</script>

<style scoped>
.fact {
  width: 40vw;
  height: 100vh;
  border: 0.1em teal solid;
  border-radius: 1em;
  padding: 1em;
}
</style>