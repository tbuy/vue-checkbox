<template>
    <selected :answerNo="answerNo" :question="question"></selected>
</template>

<script>
    import selected from '../components/selected.vue'
    export default {
        data() {
            return {
                answerNo: ['A', 'B', 'C', 'D', 'E', 'F', 'G'],
                question: [{
                        title: '题目1',
                        type: 2,
                        options: [
                            'hhhh',
                            'rrrr',
                            'yyyy'
                        ]
                    },
                    {
                        title: '题目2',
                        type: 1,
                        options: [
                            'tt',
                            'rreerr',
                            'yyyfyy'
                        ]
                    }
                ],
            }
        },
        components: {
            selected,
        }
    }

</script>

<style scoped>


</style>
