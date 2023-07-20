<template>
    <div>
        <welcomeScreen />
        <gameArea />
    </div>
</template>

<script>
import welcomeScreen from "../welcomeScreen.vue";
import gameArea from "../gameArea.vue"
export default {
    components: {
        gameArea,
        welcomeScreen
    }
}
</script>

<style>

</style>