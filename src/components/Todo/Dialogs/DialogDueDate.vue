<template>
   
</template>

<script>
export default {
    props: ['task'],
    data() {
        return{
        date: null
        }
    },
    methods: {
   
    },
    mounted(){
        if (this.task.dueDate){
            this.date = this.task.dueDate
        }
    }
}
</script>

<style>

</style>