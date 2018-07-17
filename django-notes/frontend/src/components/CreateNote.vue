<template lang="pug">
  form.form-horizontal(@submit="submitForm")
    .form-group
      .col-2
        label.form-label Заглавие
      .col-10
        input.form-input(type="text" v-model="title" placeholder="Введите название заметки...")
    .form-group
      .col-2
        label.form-label Текст
      .col-10
        textarea.form-input(v-model="body" rows=8 placeholder="Введите вашу заметку...")
    .form-group
      .col-2
      .col-10
        button.btn.btn-primary(type="submit") Добавить
</template>

<script>
export default {
  name: 'create-note',
  data () {
    return {
      'title': '',
      'body': ''
    }
  },
  methods: {
    submitForm (event) {
      this.createNote()
      this.title = ''
      this.body = ''

      event.preventDefault()
    },
    createNote () {
      this.$store.dispatch('createNote', { title: this.title, body: this.body })
    }
  }
}
</script>
