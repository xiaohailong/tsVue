<template lang="pug">
    .input
        label inputDiv
        input(type="text" :value="value" @input="$emit('input', $event.target.value)")
</template>
<script lang="ts">
import { Component, Prop, Vue,Watch} from 'vue-property-decorator';
@Component
export default class InputDiv extends Vue {
    @Prop() private value!:string;
}
</script>
