<template>
  <div class="card card-w70">

    <h3 v-if="resumeItems.length === 0">Добавьте первый блок, чтобы увидеть результат</h3>

    <component v-else :is="'app-resume-'+item.type" :content="item.content" v-for="(item, idx) in resumeItems" :key="idx"></component>

  </div>
</template>

<script>
import AppResumeAvatar from './AppResumeAvatar.vue'
import AppResumeHeader from './AppResumeHeader.vue'
import AppResumeSubheader from './AppResumeSubheader.vue'
import AppResumeText from './AppResumeText.vue'

export default {
  components: { AppResumeHeader, AppResumeAvatar, AppResumeSubheader, AppResumeText },

  props: {
    resumeItems: Array
  }

}
</script>
