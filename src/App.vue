<template>
  <div id="app">asdf
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<scirpt>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default{
  components: { 'TodoHeader':TodoHeader
              , 'TodoInput':TodoInput
              , 'TodoList':TodoList
              , 'TodoFooter':TodoFooter
  }

}
</script>

<style>
  body{
        text-align:center;
        background-color: #F6F6F8;
    }
    input{
        border-style: groove;
        width:200px;
    }
    button{
        border-style: groove;
    }
    .shadow{
        box-shadow: 5px 10px 
    }
<style>