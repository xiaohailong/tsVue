<template lang="pug">
    .temp_wraper {{data.templateContent}}
        .temp_con
            .view(@click.self="viewClick") view 
            .edit(@click.self="editClick") edit
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import TempList from '@/objects/TempList';
@Component
export default class Temp extends Vue {
  @Prop() private data!: TempList;

  private viewClick():void{
      this.$emit('listenTemp',this.data)
  }
  private editClick():void{
      this.$emit('editEvent');
  }
}
</script>

<style lang="stylus" scoped>
.temp_wraper
    display inline-block
    margin-right 40px
    width 200px
    height 300px
    background rgba(0,0,0,0.5)
    position relative
    .temp_con
        position absolute
        top 50%
        left 50%
        transform translate(-50%,-50%)
        padding 5px
        background #fff
        .view,.edit 
            border-radius 5px
            background blue
            color #fff
            cursor pointer
            padding 5px 10px
            margin-bottom 10px
</style>

