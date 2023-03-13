<template>
  <div id="selectInputField" class="grid grid-cols-2 gap-6">
    <div>
      <p class="font-[600] text-[#14171F] leading-5 mb-1">{{ label }}</p>
      <select
        v-model="benefitValue"
        class="text-[#667499] w-full px-4 py-3 rounded-lg border border-[#C2C7D6]"
      >
        <option value="" class="text-[#667499]">Select</option>
        <option v-for="(option, i) in options" :key="i">{{ option }}</option>
      </select>
    </div>
    <div>
      <label>
        <p class="font-[600] text-[#14171F] leading-5 mb-1">Amount</p>
        <p class="absolute top-0 text-[#FFFFFF]">$</p>
        <div class="flex gap-1">
          <input
            type="number"
            min="0"
            placeholder="0"
            v-model="amountValue"
            class="w-[100%] px-4 py-3 rounded border border-[#C2C7D6] placeholder:text-[#667499] placeholder:font-normal"
          />
          <select
            v-model="currencyValue"
            class="relative w-[37%] bg-[#080056] pl-4 pr-4 py-3 text-[#FFFFFF] rounded"
          >
            <option value="">$</option>
            <option>N</option>
          </select>
        </div>
      </label>
    </div>
  </div>
</template>
<script lang="ts">
export default {
  name: 'selectInputField',
  props: ['label', 'options', 'benValue', 'amtValue', 'curValue'],
  computed: {
    benefitValue: {
      get(): string {
        return this.benValue
      },
      set(value: string) {
        this.$emit('update:benValue', value)
      }
    },
    amountValue: {
      get(): number {
        return this.amtValue
      },
      set(value: number) {
        this.$emit('update:amtValue', value)
      }
    },
    currencyValue: {
      get(): string {
        return this.curValue
      },
      set(value: string) {
        this.$emit('update:curValue', value)
      }
    }
  }
}
</script>
