<template>
  <div id="genericInputField">
    <label>
      <p class="font-semibold text-[#14171F] leading-5 mb-1">
        {{ label }}<span v-if="isOptional" class="text-[#667499] ml-[6px]">(optional)</span>
      </p>
      <input
        placeholder="Enter"
        :type="type"
        v-model="inputValue"
        class="w-full px-4 py-3 rounded-lg border border-[#C2C7D6] placeholder:text-[#667499] placeholder:font-normal"
      />
    </label>
  </div>
</template>

<script lang="ts">
export default {
  name: 'genericInputField',
  props: ['label', 'type', 'isOptional', 'modelValue'],
  computed: {
    inputValue: {
      get(): string | number {
        return this.modelValue
      },
      set(value: string | number) {
        this.$emit('update:modelValue', value)
      }
    }
  }
}
</script>
