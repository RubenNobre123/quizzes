<script>
import CardQuestion from './CardQuestion.vue'
import CardQuestionChoices from './CardQuestionChoices.vue'

export default {
    name: "Card",
    emits: ['previous', 'next'],
    data() {
        return {}
    },
    props: {
        question: {
            type: Object,
            default: null
        },
        count: Number,
        length: Number
    },
    components: {
        CardQuestion,
        CardQuestionChoices
    }
}
</script>

<template>
  <div class="card-container">
    <div class="card">
      <card-question :title="question.question"/>
      <div class="previous-button">
        <span @click="$emit('previous')">&lt;</span>
      </div>
      <card-question-choices :options="question.distractors" :answer="question.answer" />
      <div class="next-button">
        <span @click="$emit('next')">&gt;</span> 
      </div>
      <div class="count">
        {{ `${count+1}/${length}` }}
      </div>
    </div>
  </div>
</template>

<style scoped>
span {
    padding: 4px;
    cursor: pointer;
    transition: font-size 0.1s;
}

span:hover {
    font-size: 37px;
}
</style>