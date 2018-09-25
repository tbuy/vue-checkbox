<template>
    <div class="demo">
        <selected :answerNo="answerNo" :question="question"></selected>
    </div>
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
                            '选项1',
                            '选项2',
                            '选项3'
                        ]
                    },
                    {
                        title: '题目2',
                        type: 1,
                        options: [
                            '选项1',
                            '选项2',
                        ]
                    },
                    {
                        title: '题目3',
                        type: 1,
                        options: [
                            '选项1',
                            '选项2',
                        ]
                    },
                    {
                        title: '题目4',
                        type: 2,
                        options: [
                            '选项1',
                            '选项2',
                            '选项3'
                        ]
                    }
                ],
            }
        },
        components: {
            selected,
        },
    }

</script>

<style scoped>
    .demo {
        margin: 30px auto;
        border: 1px solid #CCC;
        width: 300px;
        padding: 20px 30px;
        height: 400px;
        overflow: auto;
    }

</style>
