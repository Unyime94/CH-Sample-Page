<template>
  <div id="radioInputField">
    <p class="text-[#14171F] text-sm leading-5 font-semibold mb-3">
      {{ label }}
    </p>
    <div class="flex gap-6 items-center text-sm">
      <div class="flex items-center">
        <input
          type="radio"
          id="daily"
          value="Daily"
          name="billingPreference"
          v-model="inputValue"
          class="mr-2 h-6 w-6 accent-[#FE4D3C] border-[#C2C6D6]"
        />
        <label for="daily">Daily</label>
      </div>
      <div class="flex items-center">
        <input
          type="radio"
          id="weekly"
          value="Weekly"
          name="billingPreference"
          v-model="inputValue"
          class="mr-2 h-6 w-6 accent-[#FE4D3C]"
        />
        <label for="weekly">Weekly</label>
      </div>
      <div class="flex items-center">
        <input
          type="radio"
          id="biweekly"
          value="Bi-weekly"
          name="billingPreference"
          v-model="inputValue"
          class="mr-2 h-6 w-6 accent-[#FE4D3C]"
        />
        <label for="biweekly">Bi-weekly</label>
      </div>
      <div class="flex items-center">
        <input
          type="radio"
          id="monthly"
          value="Monthly"
          name="billingPreference"
          v-model="inputValue"
          class="mr-2 h-6 w-6 accent-[#FE4D3C]"
        />
        <label for="Monthly">Monthly</label>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'radioInputField',
  props: ['label', 'modelValue'],
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
