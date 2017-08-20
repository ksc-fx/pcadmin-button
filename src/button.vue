<!-- 调用说明
    <button-ele @click="buttonClick">默认实心按钮</button-ele>
    <button-ele @click="buttonClick"  :radius="false" :params="1" type="primary" color="orange" :disabled="true">橘色</button-ele>
-->
<!-- 参数说明 -->
<!-- 
type: String  类型，default:实心按钮白字，primary:白底按钮字体带颜色，text:字体按钮 （默认default）
color: String 颜色，green:绿色,red:红色,orange:橙色,blue:蓝色（默认green）
disabled: Boolean 是否有效可点击，false:可点击，true:不可点击
params: 点击返回的参数，给什么返回什么。没有就返回事件
buttonClick: function 点击回调函数  必须
-->
<template>
 <button
    class="button" __vuec__
    @click="handleClick"
    :disabled="disabled"
    :class="[
        type ? 'button-' + type : '',
        color ? 'button-' + color : '',
        radius ? '' : 'button-noradius',
        disabled ? 'is-disabled' : ''
    ]"

>
    <span><slot></slot></span>
</button> 
</template>
<style lang="less">
    // @import '../../assets/css/mixin';
    @whiteColor: #ffffff;
    @greenColor: #1EC773;
    @blueColor: #00B0E5;
    @redColor: #FF0000;
    @orangeColor: #FF930F;
    @disabledColor: #E1E1E1;

    // 函数begin
    .button-default-function(@color) {
        color: @whiteColor;
        background-color: @color;
        border-color: @color;
    }
    .button-primary-function(@color) {
        background-color: @whiteColor;
        color: @color;
        border-color: @color;
    }
    .button-text-function(@color) {
        color: @color;
    }
    // 函数end

    .button[__vuec__] {
        line-height: 1;
        height: 37px;
        padding: 10px 18.5px;
        border-radius: 7px;
        font-size: 15px;
        border-width: 1px;
        border-style: solid;
        background-color: @whiteColor;
        position: relative;
        cursor: pointer;
        &.is-disabled {
            cursor: not-allowed;
        }
        &.button-default {
            &.button-green {
                .button-default-function(@greenColor);
            }
            &.button-blue {
                .button-default-function(@blueColor);
            }
            &.button-red {
                .button-default-function(@redColor);
            }
            &.button-orange {
                .button-default-function(@orangeColor);
            }
            &.is-disabled {
                background-color: @disabledColor;
                border-color: @disabledColor;
            }
        }
        &.button-primary {
            &.button-green {
                .button-primary-function(@greenColor);
            }
            &.button-blue {
                .button-primary-function(@blueColor);
            }
            &.button-red {
                .button-primary-function(@redColor);
            }
            &.button-orange {
                .button-primary-function(@orangeColor);
            }
            &.is-disabled {
                color: @disabledColor;
                border-color: @disabledColor;
            }
        }
        &.button-text {
            padding: 0px;
            border-width: 0px;
            &.button-green {
                .button-text-function(@greenColor);
            }
            &.button-blue {
                .button-text-function(@blueColor);
            }
            &.button-red {
                .button-text-function(@redColor);
            }
            &.button-orange {
                .button-text-function(@orangeColor);
            }
            &.is-disabled {
                color: @disabledColor;
            }
        }
        &.button-default,&.button-primary {
            &.button-noradius{
                border-radius: 0px;
            }
        }
    }
</style>
<script>
    export default{
        name: "button",
        props: {
            type: {
                type: String,
                default: 'default'
            },
            color: {
                type: String,
                default: 'green'
            },
            radius: {
                type: Boolean,
                default: true,   
            },
            disabled: {
                type: Boolean,
                default: false
            },
            params: {
                default: ''
            },
        },
        data(){
            return{
            }
        },
        watch: {
        },
        computed:{
        },
        mounted() {
        },

        methods:{
            handleClick(event) {
                let params = this.params || event;
                this.$emit('click', params);
            }
        }
    }
</script>
