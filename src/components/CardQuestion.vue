<script>
export default {
    data() {
        return {}
    },
    props: {
        title: {
            type: String,
            default: null
        }
    }
}
</script>

<template>
    <div class="card-question">
        <span>{{ title }}</span>
    </div>
</template>