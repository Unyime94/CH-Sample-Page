<template>
  <div class="greyInputField">
    <label>
      <p class="font-[600] text-[#14171F] leading-5 mb-1">{{ label }}</p>
      <input
        :placeholder="placeholder"
        :type="type"
        v-model="inputValue"
        class="w-full px-4 py-3 rounded-lg bg-[#F0F4FE] placeholder:text-[#667499] placeholder:font-normal"
      />
    </label>
  </div>
</template>

<script lang="ts">
export default {
  name: 'greyInputField',
  props: ['label', 'type', 'placeholder', 'modelValue'],
  computed: {
    inputValue: {
      get(): string {
        return this.modelValue
      },
      set(value: string) {
        this.$emit('update:modelValue', value)
      }
    }
  }
}
</script>
