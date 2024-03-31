<template>
  <div>
    <div class="visible" v-if="infoVisible==false">
      <button
        @click="isVisible"
      >
      Показать информацию
      </button>
    </div>
    <div class="info" v-if="infoVisible==true">
      <button
        @click="isInvisible"
      >
        Скрыть
      </button>

      <h3>Рандомные факты о котах на каждый день</h3>
      <h5>Целью данного веб-приложения является радовать пользователей порцией интересных, а иногда неожиданных, фактов о котах</h5>
      <!-- <h1>>^_^<</h1> -->
      <h3>Справка по работе с API</h3>
      <h5>API (Application Programming Interface) — это набор правил, позволяющих одному программному продукту взаимодействовать с другим. В веб-разработки API служит мостом между пользовательским интерфейсом и сервером c базой данных.</h5>
      <h5>В данном веб-приложении в качестве API выступает сайт https://catfact.ninja/fact, с которого получается факт/массив фактов и послечего клиент отображает их на экране.</h5>
      <h3>Автора</h3>
      <h5>Пасюта Н.С., 20 годиков, студент</h5>
      <h5>Тел: 89018920298</h5>
      <h5>E-mail: pasyuta_nikita@emal.ru</h5>
    </div>
  </div>
  
</template>

<script>
export default {
  name: 'InfoForm',
  props: {
    infoVisible: Boolean
  },
  methods: {
    isVisible() {
      this.$emit('isVisible');
    },
    isInvisible() {
      this.$emit('isInvisible');
    }
  }

}
</script>

<style scoped>
.info {
  border: 0.1em teal solid;
  border-radius: 1em;
  padding: 1em;
  box-shadow: 0.1em 0.1em 1em 0.1em gray;
  width: 50vw;
  height: 100vh;
}
.visible {
  width: 50vw;
  height: 100vh;
}
</style>
