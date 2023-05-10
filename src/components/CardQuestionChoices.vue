<script>
export default {
    data() {
        return {
            done: false
        }
    },
    props: {
        options: {
            type: Array,
            default: null
        },
        answer: String
    },
    methods: {
        resolve(evt) {
            if (this.done)
                return
            if (evt.srcElement.__vnode.children == this.answer)
                 evt.target.parentElement.classList.add("correct")
            else {
                evt.target.parentElement.classList.add("wrong")
                let correct = Array.from(document.getElementsByTagName("span")).find(s => s.textContent == this.answer)
                correct.parentElement.classList.add("correct")
            }
            this.done = true
        },
        reset() {
            Array.from(document.getElementsByClassName("wrong")).forEach(el => el.classList.remove("wrong"))
            Array.from(document.getElementsByClassName("correct")).forEach(el => el.classList.remove("correct"))
            this.done = false
        }
    },
    watch: {
        $props: {
            handler() {
                this.reset() 
            },
            deep: true
        }
    }
}
</script>

<template>
    <div class="card-question-choices">
        <ul>
            <li v-for="opt in options" @click="showAnswer">
                <span @click="resolve">{{ opt }}</span>
            </li>
        </ul>
    </div>
</template>

<style scoped>
ul {
  list-style: none;
  padding-inline-start: 20px;
  padding-inline-end: 20px;
}

li {
    font-size: 18px;
    margin: 10px 0;
    cursor: pointer;
}

ul li::before {
  content: "❓";
  display: inline-block;
  margin-right: 0.5rem;
}

li.wrong::before {
    content: "❌"
}

li.correct::before {
    content: "✔️"
}

span {
    cursor: pointer;
}
</style>