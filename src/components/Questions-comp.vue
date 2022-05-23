<template>
  <div class="questions-ctr">
        <div class="progress">
            <div class="bar" :style= "{width: `${(questionsAnswered / questions.length) * 100}%`}"></div>
            <div class="status">{{questionsAnswered}} out of {{questions.length}} questions answered</div>
        </div>
        <div class="single-question" v-for = "(question, index) in questions" :key="question.q" v-show = "questionsAnswered === index">
            <div class="question">{{question.q}}</div>
            <div class="answers">
                <div class="answer" @click.prevent="selectAnswer(answer.is_correct)" v-for = "answer in question.answers" :key="answer.text">{{answer.text}}</div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
name: "Questions-comp",
props: ["questions", "questionsAnswered"],
emits:["selectAnswer"],
methods:{
    selectAnswer(is_correct){
this.$emit("selectedAnswer", is_correct)
    }
}
}

</script>

<style>

</style>