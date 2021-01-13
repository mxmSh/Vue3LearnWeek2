<template>

  <div class="card">
    <h2>Комментарии</h2>
    <ul class="list">

      <li class="list-item" v-for="comment in commetsList" :key="comment.id">
        <app-comment>
          <template #email>
            {{ comment.email }}
          </template>
          <template #text>
            {{ comment.name }}
          </template>
        </app-comment>
      </li>

    </ul>
  </div>

</template>

<script>
import AppComment from './AppComment.vue'

export default {
  components: { AppComment },
  props: {
    commetsList: Array
  }

}
</script>
