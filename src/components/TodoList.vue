<template>
  <div>
    <section>
      <transition-group name="list" tag="ul">
        <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
          <i class="checkBtn fas fa-check" aria-hidden="true"></i>
          {{todoItem}}
          <span class="removeBtn" type="button" @click="showConfirmModal(todoItem, index)">
            <i class="far fa-trash-alt" aria-hidden="true"></i>
          </span>
        </li>
      </transition-group>
    </section>
    <div class="inputBox shadow">
      <modal v-if="showModal" @close="showModal = true">
              <h3 slot="header">삭제</h3>
              <!-- body 입력안하면 default body 튀어나옴 -->
              <span slot="body">
                  삭제 하시겠습니까?
              </span>
              <span slot="footer" @click="showModal = false">
                  <i class="closeModalBtn fas fa-yes" aria-hidden="true" @click="removeTodo()">네</i>
                  &nbsp;&nbsp;&nbsp;&nbsp;
                  <i class="closeModalBtn fas fa-no" aria-hidden="true">아니오</i>
              </span>
        </modal>
    </div>
  </div>
</template>

<script>
var selTodoItem = '';
var selIndex    = '';
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
    removeTodo(){
      this.$emit('removeTodo', selTodoItem, selIndex);
    },
    showConfirmModal(todoItem, index){
      this.showModal = !this.showModal;
      selTodoItem =todoItem;
      selIndex =index;
    }
  },
  components:{
      Modal  : Modal
  }
}
</script>

<style>
  ul{
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }

  li{
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }

  .checkBtn{
    line-height: 45px;
    color:#62acde;
    margin-right: 5px;
  }

  .removeBtn{
    margin-left: auto;
    color: #de4343;
  }

  .list-enter-active, list-leave-active{
    transition: all 1s;
  }
  .list-enter, list-leave-to{
    opacity: 0;
    transform :translateY(30px);
  }
</style>