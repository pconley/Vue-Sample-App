<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>

    <todo 
    	v-on:delete-todo="deleteTodo" 
    	v-on:complete-todo="completeTodo" 
    	v-for="(todo, index) in todos" 
    	v-bind:todo="todo" 
    	v-bind:index="index" 
    	:key="todo.id">
    </todo>

  </div>
</template>

<script type = "text/javascript" >

	import Todo from './Todo';

	export default {
	  props: ['todos'],
	  components: { Todo },
	  methods: {
	    deleteTodo(todo) {
	      console.log('*** delete in the list');
	      const todoIndex = this.todos.indexOf(todo);
	      this.todos.splice(todoIndex, 1);
	    },
	    completeTodo(todo) {
	      console.log('*** complete in the list');
	      const todoIndex = this.todos.indexOf(todo);
	      this.todos[todoIndex].done = true;
	    },
	  },
	};

</script>