<template lang="pug">
  .home
    temp(v-for="item in tempItems" :key="item.templateId" :data="item" @listenTemp="getTemp" @editEvent="showlog(item)")
    temp-preview(v-if="showPreview" @listenPreview="previewEvent" @editEvent="previewShowLog")
    login(:inputValue.sync="inputValue1") 
    input(type="text" v-model="inputValue1")

    input-div(v-model="inputDivValue")
    .input {{inputDivValue}}
    
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import Temp from "@/components/temp.vue"
import TempPreview from "@/components/tempPreview.vue"
import TempList from '@/objects/TempList';
import Login from "@/components/login.vue"
import InputDiv from "@/components/InputDiv.vue"
@Component({
  components: {
    Temp,
    TempPreview,
    Login,
    InputDiv 
  },
})
export default class Home extends Vue {
  private inputValue1:string = '123';
  private showPreview:boolean = false;
  private currTemp!:TempList;
  private inputDivValue:string='123';
  private tempItems:Array<TempList> = [
    {
      templateId:1,
      templateContent:'template 1'
    },{
      templateId:2,
      templateContent:'template 2'
    }
  ]
  private getTemp(val:TempList):void{
    this.currTemp = val;
    this.showPreviewChange();
  }
  private previewEvent():void{
    this.showPreviewChange()
  }
  private showlog(item:TempList):void{
    alert(item.templateContent)
  }
  private previewShowLog():void{
    alert(this.currTemp.templateContent)
  }
  private showPreviewChange():void{
    this.showPreview =!this.showPreview;
  }
}
</script>
