<template>
    <div>
        <btn>默认按钮</btn>
        <btn type="primary">primary</btn>
        <btn type="info">info</btn>
        <btn type="success">success</btn>
        <btn type="warning">warning</btn>
        <btn type="danger">danger</btn>
        <btn :disabled="true">不可点击</btn>
    </div>
</template>

<style lang="less">
</style>

<script>

import btn from '../src/button.vue';

export default {
    data () {
        return {
        };
    },
    mounted() {
    },
    methods: {
    },
    components: {
        btn
    }
};
</script>

