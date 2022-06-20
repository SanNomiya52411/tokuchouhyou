<template>
    <p>ダイス１:{{ JobSkill }}</p>
    <p>ダイス２:{{ HobbySkill }}</p>
</template>

<script>
export default {
    props: {
        JobSkill: Number,
        HobbySkill: Number
    }
}
</script>