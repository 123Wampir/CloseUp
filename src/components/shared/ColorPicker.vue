<template>
    <div class="color">
        <label v-if="hideHex == false" :for="props.id">{{ model }}</label>
        <div class="button" :class="props.readonly == true ? 'readonly' : ''">
            <label class="theme" :style="`background:${model}`" :title="props.title" :id="props.id">
                <input type="color" v-model="model" :id="props.id" :readonly="props.readonly" :disabled="props.readonly"
                    @change="emits('change', $event)" @input="emits('input', $event)">
            </label>
        </div>
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{
    title?: string,
    id?: string
    readonly?: boolean
    hideHex?: boolean
}>();
const model = defineModel();

const emits = defineEmits<{
    "change": [value: Event],
    "input": [value: Event]
}>();

</script>

<style scoped>
.color {
    display: flex;
    flex-direction: row;
    align-items: center;
}

.button {
    width: 1rem;
    height: 1rem;
    border-radius: 100%;
    border: 1px solid var(--color-border);
    padding: 0;
}

.button>* {
    width: 100%;
    height: 100%;
    border-radius: 100%;
}

.readonly:hover {
    border: none;
}

input {
    width: 0;
    height: 0;
    opacity: 0;
}
</style>