<template>
 <button
    class="button"
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
<style lang="less" scoped>
    @whiteColor: #ffffff;
    
    @import '~pcadmin-base/src/css/var.less';

    // 函数begin
    .button-default-function(@color) {
        color: @whiteColor;
        background-color: @color;
        border-color: @color;
    }
    .button-primary-function(@color) {
        color: @color;
        border-color: @color;
    }
    .button-text-function(@color) {
        color: @color;
    }
    // 函数end

    .button {
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
                .button-default-function(@infoColor);
            }
            &.button-blue {
                .button-default-function(@successColor);
            }
            &.button-red {
                .button-default-function(@dangerColor);
            }
            &.button-orange {
                .button-default-function(@warningColor);
            }
            &.is-disabled {
                background-color: @disabledColor;
                border-color: @disabledColor;
            }
        }
        &.button-primary {
            &.button-green {
                .button-primary-function(@infoColor);
            }
            &.button-blue {
                .button-primary-function(@successColor);
            }
            &.button-red {
                .button-primary-function(@dangerColor);
            }
            &.button-orange {
                .button-primary-function(@warningColor);
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
                .button-text-function(@infoColor);
            }
            &.button-blue {
                .button-text-function(@successColor);
            }
            &.button-red {
                .button-text-function(@dangerColor);
            }
            &.button-orange {
                .button-text-function(@warningColor);
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
        name: 'button',
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
                default: true
            },
            disabled: {
                type: Boolean,
                default: false
            },
            params: {
                default: ''
            }
        },
        data () {
            return {
            };
        },
        watch: {
        },
        computed: {
        },
        mounted () {
        },

        methods: {
            handleClick (event) {
                let params = this.params || event;
                this.$emit('click', params);
            }
        }
    };
</script>
