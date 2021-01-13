<template>

  <div class="container column">  
    <app-edit-form @addItem="addItemToResume"></app-edit-form>
    <app-resume :resumeItems="resume"></app-resume>
  </div>

  <div class="container">
    <p>
      <app-button @press="loadComments">Загрузить комментарии</app-button>
    </p>

    <app-comments-list :commetsList="comments" v-if="commentsFlag === 2"></app-comments-list>

    <app-loader v-else-if="commentsFlag === 1"></app-loader>

  </div>
</template>

<script>
import axios from 'axios'
import AppButton from './components/AppButton.vue'
import AppCommentsList from './components/AppCommentsList.vue'
import AppEditForm from './components/AppEditForm'
import AppResume from './components/AppResume.vue'
import AppLoader from './components/AppLoader.vue'

export default {
  components: { AppEditForm, AppResume, AppCommentsList, AppButton, AppLoader },
  
  data() {
    return {
      resume: [],
      comments: [],
      commentsFlag: 0  // 0 - блок скрыт, 1 - прогресс, 2 - блок комментариев
    }
  },

  methods: {
    addItemToResume (data) {
      this.resume.push(Object.assign({}, data))
    },

    async loadComments() {
      this.commentsFlag = 1
      const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = data
      this.commentsFlag = 2

    }
  }


}

</script>
