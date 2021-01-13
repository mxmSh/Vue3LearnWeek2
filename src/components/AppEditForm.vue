<template>
  <form class="card card-w30" @submit.prevent="addItem">

    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="item.type">
        <option value="header">Заголовок</option>
        <option value="subheader">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model.trim="item.content"></textarea>
    </div>
    
    <button class="btn primary" :disabled="isAddButtonDisabled" type="submit">Добавить</button>

  </form>
</template>

<script>
import { computed } from 'vue'

export default {
  emits: [ 'addItem' ],
  data() {
    return {
      item: {
        type: 'header',
        content: ''
      }
    }
  },

  methods: {
    addItem () {
      this.$emit('addItem', this.item)
      this.item.type = 'header'
      this.item.content = ''
    }
  },

  computed: {
    isAddButtonDisabled() {
      return this.item.content.length < 4
    }
  }

}
</script>
