<template>
    <div class="selected">
        <div class="selected-item" v-for="(item,index) in question" :key="item.id">
            <div class="item-title">
                <span>{{ questionNo.length ? questionNo[index] : index + 1 }}. </span>
                <span>{{ item.title }}</span>
                <span>{{ item.type == 1? '(单选)': '(多选)'}}</span>
            </div>
            <div class="item-option" v-for="(val,i) in item.options" :key="val.id">
                <div v-if="item.type == 1">
                    <input type="radio" v-model="item.selected" :value="val" :id="(index+1)+answerNo[i]+i">
                    <label class="radio" :for="(index+1)+answerNo[i]+i"><s></s></label>
                    <label :for="(index+1)+answerNo[i]+i"><span>{{ answerNo[i] }}. </span><span>{{ val }}</span></label>
                </div>
                <div v-else>
                    <input type="checkbox" v-model="item.selected" :value="val" :id="(index+1)+answerNo[i]+i">
                    <label class="checkbox" :for="(index+1)+answerNo[i]+i"><i></i></label>
                    <label :for="(index+1)+answerNo[i]+i"><span>{{ answerNo[i] }}. </span><span>{{ val }}</span></label>
                </div>
            </div>
        </div>
        <div class="submit" @click="submit" :style="{backgroundColor: isBtnHeight? 'red': '#ccc'}">提交</div>
    </div>
</template>

<script>
    export default {
        props: {
            questionNo: {
                type: Array,
                default: () => [],
                required: false
            },
            answerNo: {
                type: Array,
                default: () => [],
                required: true
            },
            question: {
                type: Array,
                default: () => [],
                required: true
            },
        },
        computed: {
            isBtnHeight() {
                return this.question.every(item => item.selected && item.selected.length)
            }
        },
        methods: {
            submit() {
                var _reault = [];
                this.question.forEach(item => {
                    _reault.push(item.selected)
                    if (item.type == 1) {
                        this.$set(item, 'selected', '')
                    } else {
                        this.$set(item, 'selected', [])
                    }
                })

                this.$emit('submit', _reault)
            }
        },
        mounted() {
            this.question.forEach(item => {
                if (item.type == 1) {
                    this.$set(item, 'selected', '')
                } else {
                    this.$set(item, 'selected', [])
                }
            })
        }
    }

</script>

<style scoped>
    input[type='checkbox'] {
        width: 16px;
        height: 16px;
        vertical-align: middle;
        display: none;
    }

    input[type='radio'] {
        width: 16px;
        height: 16px;
        vertical-align: middle;
        display: none;
    }

    input[type='checkbox']:not(:checked)+.checkbox>i {
        display: inline-block;
        width: 16px;
        height: 16px;
        vertical-align: middle;
        background: url("../assets/check-n.png") no-repeat 0 0;
        background-size: 100%;
    }

    input[type='checkbox']:checked+.checkbox>i {
        display: inline-block;
        width: 16px;
        height: 16px;
        vertical-align: middle;
        background: url("../assets/check-y.png") no-repeat 0 0;
        background-size: 100%;
    }

    input[type='radio']:not(:checked)+.radio>s {
        display: inline-block;
        width: 16px;
        height: 16px;
        vertical-align: middle;
        background: url("../assets/radio-n.png") no-repeat 0 0;
        background-size: 100%;
        cursor: pointer;
    }

    input[type='radio']:checked+.radio>s {
        display: inline-block;
        width: 16px;
        height: 16px;
        background: url("../assets/radio-y.png") no-repeat 0 0;
        background-size: 100%;
        vertical-align: middle;
        cursor: pointer;
    }

    .selected-item {
        margin-bottom: 20px;
        font-size: 16px;
    }

    .selected-item>.item-title {
        margin-bottom: 10px;
    }

    .selected-item>.item-option {
        font-size: 14px;
        margin-bottom: 5px;
        line-height: 20px;
    }

    .selected-item>.item-option span {
        font-size: 14px;
        vertical-align: middle;
        margin-left: 5px;
    }

    .submit {
        background-color: red;
        cursor: pointer;
        width: 100px;
        height: 30px;
        line-height: 25px;
        text-align: center;
        color: #fff;
        margin: 0 auto;
    }

</style>
