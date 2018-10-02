<template>
    <div class="demo">
        <div class="component">
            <selected :answerNo="answerNo" :question="question" @submit="submit"></selected>
        </div>
        <div class="reault">
            <div class="h3">选择结果: </div>
            <div v-for="(item,index) in reault" :key="item.id" class="item">
                <span>{{ index + 1 }}. </span>
                <span>{{ item }}</span>
            </div>
        </div>
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
                reault: []
            }
        },
        components: {
            selected,
        },
        methods: {
            submit(val) {
                this.reault = val;
            }
        }
    }

</script>

<style scoped>
    .demo {
        margin: 30px auto;
        border: 1px solid #CCC;
        width: 600px;
        padding: 20px 30px;
        box-sizing: border-box;
        height: 530px;
        overflow: auto;
        display: flex;
    }

    .component {
        width: 50%;
        border-right: 1px solid #CCC;
        box-sizing: border-box;
    }

    .reault {
        width: 50%;
        padding-left: 20px;
        box-sizing: border-box;
    }

    .item {
        margin-top: 10px;
    }

</style>
