<template>
 <button
    class="ks-button"
    :disabled="disabled"
    :class="[
        type ? 'button-' + type : '',
        disabled ? 'is-disabled' : ''
    ]"
>
    <span><slot></slot></span>
</button> 
</template>
<style lang="less" scoped>
    @ksPrefix: ks-;
    @import '~pcadmin-base/src/css/var.less';

    .@{ksPrefix}button {
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

        // 函数begin
        .ks-button-default-function(@color) {
            color: @whiteColor;
            background-color: @color;
            border-color: @color;
        }
        .ks-button-primary-function(@color) {
            color: @color;
            border-color: @color;
        }
        // 函数end

        &.is-disabled {
            cursor: not-allowed;
        }
        &.button-primary {
            .ks-button-primary-function(@primaryColor);
        }
        &.button-info {
            .ks-button-default-function(@infoColor);
        }
        &.button-success {
            .ks-button-default-function(@successColor);
        }
        &.button-danger {
            .ks-button-default-function(@dangerColor);
        }
        &.button-warning {
            .ks-button-default-function(@warningColor);
        }
        &.is-disabled {
            background-color: @disabledColor;
            border-color: @disabledColor;
            color: @whiteColor;
        }
    }
</style>
<script>
    export default{
        name: 'button',
        props: {
            type: {
                type: String,
                default: 'primary'
            },
            disabled: {
                type: Boolean,
                default: false
            }
        }
    };
</script>
