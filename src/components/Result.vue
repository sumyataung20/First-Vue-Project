<template>
    <p>Result is {{score}}ms</p>

    <div v-if = "score < 250">
        <p>You are too fast like a flash!!</p>
    </div>

    <div v-else-if = "score > 200 && score < 500">
        <p>You are normal</p>
    </div>

    <div v-else>
        <p>You are too slow</p>
    </div>
</template>

<script>
export default {
    props: ["score"]

}
</script>

<style>

</style>