<template>
<div>
 
<list-header bgColor="bg-light-blue-9">TODO</list-header>

		<q-list
		separator
		bordered>

			<task
			v-for="(task, key) in tasksTodo"
		  	:key="key"
		  	:task="task"
		  	:id="key"></task>

		</q-list>
</div>		
</template>

<script>
    export default {
        props: ['tasksTodo'],
        components: {
 			'task' : require('components/Task.vue').default,
 			'list-header' : require('components/ListHeader.vue').default,
        }
    }
</script>