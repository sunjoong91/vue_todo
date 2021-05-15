<template>
  <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="내용을 입력하세요." v-on:keyup.enter="addTodo">
        <!--<button v-on:click="addTodo">추가</button>-->
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>

        <modal v-if="showModal" @close="showModal = false">
            <h3 slot="header">경고</h3>
            <!-- body 입력안하면 default body 튀어나옴 -->
            <span slot="body"></span>
            <span slot="footer" @click="showModal = false">
                {{message}}
                <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
            </span>
        </modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'


export default{
    props: ['propsdata'],
    data(){
        return{
            newTodoItem: '',
            showModal: false
        }
    },
    methods:{
        addTodo(){
            var value = this.newTodoItem;
            if(value != ""){
                this.$emit('addTodo',value);
                this.clearInput();
            }else{
                this.showModal = !this.showModal;
                this.message = '할 일을 입력하세요.'
            }
        },
        clearInput(){
            this.newTodoItem = '';
        }
    },
    components:{
        Modal  : Modal
    }
}
</script>

<style scoped>
    input:focus{
        outline:none;
    }
    .inputBox{
        background: white;
        height: 50px;
        line-height: 50px;
        border-radius: 5px;
    }
    .inputBox input{
        border-style: none;
        font-size:0.9rem;
    }
    .addContainer{
        float: right;
        background: linear-gradient(to right, #6478FB, #8763FB);
        display: black;
        width:3rem;
        border-radius:0 5px 5px 0;
    }
    .addBtn{
        color:white;
        vertical-align:middle;
    }

    .fa-yes{
        content: "네";
    }

    .fa-no{
        content: "아니오";
    }

</style>