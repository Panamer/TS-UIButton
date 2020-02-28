<template>
    <!-- v-on="$listeners" -->
    <button class="ui-btn" @click="onClickBtn"
        :class="{
            'ui-btn-xsmall': xsmall,
            'ui-btn-small': small,
            'ui-btn-large': large,
            'ui-btn-xlarge': xlarge
        }"
    >
        <slot>button</slot>
    </button>
</template>

<script lang="ts">
// UIButton
import {Component, Vue, Emit, Prop } from 'vue-property-decorator';

@Component
export default class UIButton extends Vue {

    @Prop(Boolean) private xsmall: boolean | undefined
    @Prop(Boolean) private small: boolean | undefined
    @Prop(Boolean) private large: boolean | undefined
    @Prop(Boolean) private xlarge: boolean | undefined

    @Emit('click') private emitClickEvent(event: MouseEvent) {
        // do nothing
    }
    private onClickBtn(event: MouseEvent) {
        this.emitClickEvent(event)
    }

    mounted() {
        console.log(this.large);   // 结果是true
    }
}
        // cursor not-allowed
</script>
<style lang="stylus" scoped>
resize(minWidth, height, paddingLR, fontSize) {
    min-width minWidth
    height height
    padding 0 paddingLR
    font-size fontSize
    border-radius (@height / 2)
}
.ui-btn
    resize(64px, 36px, 16px, .875rem)
    border 0 solid black
    border-radius 4px
    color #17233d
    background-color #2d8cf0
    font-weight 500
    letter-spacing .1rem
    cursor pointer
    user-select none
    outline none
    &:hover
        filter brightness(120%)
    &:active
        filter brightness(80%)
    &.ui-btn-xsmall
        resize(36px, 20px, 9px, 0,625rem)
    &.ui-btn-small
        resize(50px, 28px, 12px, 0.75rem)
    &.ui-btn-large
        resize(78px, 44px, 19px, .875rem)
    &.ui-btn-xlarge
        resize(92px, 52px, 23px, 1rem)
</style> 