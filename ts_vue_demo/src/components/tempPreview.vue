<template lang="pug">
    .mask(@click.self="previewClick")   
        .con    
            .edit(@click.self="editClick") edit
            .cancel(@click.self="previewClick") cancel
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class TempPreview extends Vue {
  @Prop() private msg!: string;
  private previewClick():void{
      this.$emit('listenPreview')
  }
  private editClick():void{
      this.$emit('editEvent');
  }
}
</script>

<style lang="stylus">
.mask   
    position fixed
    top 0 
    left 0
    background rgba(0,0,0,0.5)
    width 100%
    height 100%
    .con  
        width 200px
        height 300px
        position absolute
        top 50%
        left 50%
        transform translate(-50%,-50%)
        background #fff
        .edit,.cancel 
            padding 5px 10px
            background blue
            color #ffffff
            border-radius 5px
            margin 20px 0
</style>