<script>
import Card from './components/Card.vue'
import quizzes from './quizzes.json'

export default {
  components: {
    Card
  },
  data() {
    return {
      count: 0,
      quizzes:  quizzes["quizzes"]
    }
  }
}
</script>

<template>
    <Card v-if="quizzes != null" :question="quizzes[count]" :count="count" :length="quizzes.length" @previous="count = Math.max(0, count-1)" @next="count = Math.min(count+1, quizzes.length-1)"/>
</template>
