<template>
  <!-- <div>list</div> -->
  <section>
    <ul>
    <!-- 하나씩 하드코딩하는것은 비효율적이기 때문에 로컬스토리지를 이용하여 효율적으로 관리한다. -->
      <!-- <li>할일 1</li>
      <li>할일 2</li>
      <li>할일 3</li> -->

      <!-- <li v-for="(todoItem, index) in todoItems" :key="todoItem" class="shadow" > -->
      <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow" >

        <i class="checkBtn fa fa-check" aria-hidden="true"></i>
        {{todoItem}}
        <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
        <i class="fa fa-trash-o" aria-hidden="true"></i>
        </span>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  props: ['propsdata'],
  // data() {
  //   return {
  //     todoItems: []
  //   }
  // },
  methods: {
    removeTodo(todoItem, index) {
            // console.log("click")
            // console.log(todoItem, index)
            // localStorage.removeItem(todoItem);
            // this.todoItems.splice(index,1); 
            // 배열의 특정 인덱스를 삭제

            this.$emit('removeTodo', todoItem, index);
        }
    },

  // created(){
  //   if(localStorage.length > 0) {
  //     for (var i=0; i < localStorage.length; i++){
  //       this.todoItems.push(localStorage.key(i)); 
  //       // 로컬스토리지의 내용을 todoItems 리스트에 담는다.
  //     }
  //   }
  // },

}
</script>

<style>
  ul {
    /* 목록 아이템의 스타일을 지정 */
    list-style-type: none; 

    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }

  li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }

  .checkBtn {
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
  }

  .removeBtn {
    margin-left: auto;
    color: #de4343;
  }
</style>