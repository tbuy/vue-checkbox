<template>
    <div class="selected">
        <div class="item" v-for="(item,index) in question" :key="item.id">
            <div class="item-title">
                <span>{{ questionNo.length ? questionNo[index] : index + 1 }}. </span>
                <span>{{ item.title }}</span>
                <span>{{ item.type == 1? '(单选)' + radio: '(多选)' + selected}}</span>
            </div>
            <div class="item-option" v-for="(val,i) in item.options" :key="val.id">
                <div v-if="item.type == 1">
                    <input type="radio" v-model="radio" :value="val" :id="(index+1)+answerNo[i]+i">
                    <label class="radio" :for="(index+1)+answerNo[i]+i"><s></s></label>
                    <label :for="(index+1)+answerNo[i]+i"><span>{{ answerNo[i] }}. </span><span>{{ val }}</span></label>
                </div>
                <div v-else>
                    <input type="checkbox" v-model="selected" :value="val" :id="(index+1)+answerNo[i]+i">
                    <label class="checkbox" :for="(index+1)+answerNo[i]+i"><i></i></label>
                    <label :for="(index+1)+answerNo[i]+i"><span>{{ answerNo[i] }}. </span><span>{{ val }}</span></label>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                selected: [],
                radio: '',

            }
        },
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
            }
        }
    }

</script>

<style scoped>
    input[type='checkbox'] {
        width: 20px;
        height: 20px;
        vertical-align: middle;
        display: none;
    }

    input[type='radio'] {
        width: 20px;
        height: 20px;
        vertical-align: middle;
        display: none;
    }

    input[type='checkbox']:not(:checked)+.checkbox>i {
        display: inline-block;
        width: 20px;
        height: 20px;
        vertical-align: middle;
        background: url("../assets/check-n.png") no-repeat 0 0;
        background-size: 100%;
    }

    input[type='checkbox']:checked+.checkbox>i {
        display: inline-block;
        width: 20px;
        height: 20px;
        vertical-align: middle;
        background: url("../assets/check-y.png") no-repeat 0 0;
        background-size: 100%;
    }

    input[type='radio']:not(:checked)+.radio>s {
        display: inline-block;
        width: 20px;
        height: 20px;
        vertical-align: middle;
        background: url("../assets/radio-n.png") no-repeat 0 0;
        background-size: 100%;
        cursor: pointer;
    }

    input[type='radio']:checked+.radio>s {
        display: inline-block;
        width: 20px;
        height: 20px;
        background: url("../assets/radio-y.png") no-repeat 0 0;
        background-size: 100%;
        vertical-align: middle;
        cursor: pointer;
    }

</style>
