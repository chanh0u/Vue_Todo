<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do"
         v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            
            <i class="addBtn fa fa-plus" aria-hidden="true"></i>
        </span>
        <!-- <button v-on:click="addTodo">추가</button> -->

        <modal v-if="showModal" @close="showModal = false">
            <h3 slot="header">경고</h3>
            <span slot="footer" @click="showModal = false">
                할 일을 입력하세요.
                <i class="closeModalBtn fa fa-times" aria-hidden="true"></i>
            </span>
        </modal>

    </div>

</template>

<script>
import Modal from './common/Modal.vue'

export default {
    props: ['propsdata'],
    data() {
        return {
            newTodoItem:"", // input박스 값 설정
            showModal: true,
        }
    },
    methods: {
        addTodo() {
            // console.log(this.newTodoItem);
            // localStorage.setItem(this.newTodoItem, this.newTodoItem); //로컬스토리지의 값 저장
            if (this.newTodoItem !=""){
                var value = this.newTodoItem && this.newTodoItem.trim(); //텍스트의 앞뒤 공백 문자열 제거
                // localStorage.setItem(value,value); // 로컬 스토리지를 통한 데이터 저장 방법 => 데이터 갱신 문제 발생!!
                this.$emit('addTodo',value);
                this.clearInput();
            } else {
                this.showModal = !this.showModal;
            }
        },
        clearInput() {
            this.newTodoItem='';
        }
    },
    components: {
        Modal : Modal
    }
}
</script>

<style scoped>
    input:focus{
        outline: none;
    }
    .inputBox{
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input {
        border-style: none;
        font-size: 0.9rem;
    }
    .addContainer {
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: inline-block;
        width: 3rem;
        border-radius: 0 5px 5px 0;
    }
    .addBtn {
        color: white;
        vertical-align: middle;
    }
</style>