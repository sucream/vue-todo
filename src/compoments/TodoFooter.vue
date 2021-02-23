<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn" @click="clearTodo">모두 지우기</span>
    </div>
</template>
<script>
export default {
    methods: {
        clearTodo: function() {
            this.$emit('removeAll');
        }
    }
}
</script>
<style>
    .clearAllContainer {
        width: 8.5rem;
        height: 50px;
        line-height: 50px;
        background-color: white;
        border-radius: 5px;
        margin: 0 auto;
    }
    .claerAllBtn {
        color: #e20303;
        display: black;
    }
</style>