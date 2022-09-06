<template>
    <!-- <div>footer</div> -->
    <!-- 모두 삭제하기 버튼을 포함하는 컴포넌트 -->
    <div class="clearAllcontainer">
        <span class="clearAllBtn" @click="clearTodo">Clear All</span>

    </div>
</template>

<script>
export default {
    methods: {
        clearTodo() {
            // console.log("테스트");
            // localStorage.clear();
            // this.todoItems = [];

            this.$emit('removeAll');
        }
    }
}
</script>

<style scoped>
    .clearAllcontainer {
        width: 8.5rem;
        height: 50px;
        line-height: 50px;
        background-color: white;
        border-radius: 5px;
        margin: 0 auto;
    }
    .clearAllBtn {
        color: #e20303;
        display: black;
    }
</style>