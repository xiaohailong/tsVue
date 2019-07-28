<template lang="pug">
    .login
        label name
        input(type="text" v-model="text")
</template>
<script lang="ts">
import { Component, Prop, Vue,Watch} from 'vue-property-decorator';
@Component
export default class Login extends Vue {
    @Prop() inputValue!:string;
    
    private text:string = '1';

    @Watch('text', { immediate: true, deep: true })
    onChange(newVal:string):void{
         this.$emit('update:inputValue', newVal)
    }

   
}
</script>
