<template>
  <div id="app">
    <div class="flex items-center ml-7 mt-6">
      <ArrowLeft class="mr-3" />
      <h1 class="text-[#080056] font-bold text-[24px] border-l pl-4 border-[#C2C7D6]">
        Set Up a Self-Funded Account
      </h1>
    </div>
    <div class="m-0 p-6">
      <form class="text-sm" @submit.prevent="handleSubmit">
        <div class="border rounded-lg border-[#C2C7D6] p-4">
          <div class="grid grid-cols-2 gap-6 w-full">
            <GreyInputField
              v-for="(ownerInput, i) in ownerInputs"
              :key="i"
              v-model="ownerInput.value"
              :label="ownerInput.label"
              :type="ownerInput.type"
              :placeholder="ownerInput.placeholder"
            />

            <GenericInputField
              v-for="(descriptionInput, i) in descriptionInputs"
              :key="i"
              v-model="descriptionInput.value"
              :label="descriptionInput.label"
              :type="descriptionInput.type"
              :isOptional="descriptionInput.isOptional"
            />
          </div>

          <RadioInputField
            :label="billingPreference.label"
            v-model="billingPreference.value"
            class="mt-6"
          />

          <h2 class="text-[#114FF5] font-normal text-base py-6">Billing Contact</h2>
          <div class="grid grid-cols-2 gap-6 w-full">
            <GenericInputField
              v-for="(billingInput, i) in billingInputs"
              :key="i"
              v-model="billingInput.value"
              :label="billingInput.label"
              :type="billingInput.type"
            />
          </div>

          <div class="mt-6 w-[50%]">
            <label>
              <p class="font-[600] text-[#14171F] leading-5 mb-1">Deductible</p>
              <p class="absolute top-0 text-[#FFFFFF]">$</p>
              <div class="flex gap-1">
                <input
                  type="number"
                  min="0"
                  placeholder="0"
                  class="w-[70%] px-4 py-3 rounded border border-[#C2C7D6] placeholder:text-[#667499] placeholder:font-normal"
                />

                <select class="relative w-[27%] bg-[#080056] pl-4 pr-4 py-3 text-[#FFFFFF] rounded">
                  <option selected>$</option>
                  <option>N</option>
                </select>
              </div>
            </label>
          </div>

          <h2 class="text-[#114FF5] font-normal text-base my-6">Medical Benefits</h2>
          <SelectInputField
            v-model:benValue="medicalBenefitInputs.benefitValue"
            v-model:amtValue="medicalBenefitInputs.amountValue"
            v-model:curValue="medicalBenefitInputs.currencyValue"
            :label="medicalBenefitInputs.label"
            :options="medicalBenefitInputs.options"
          />

          <h2 class="text-[#114FF5] font-normal text-base my-6">Vision Benefits</h2>
          <SelectInputField
            v-model:benValue="visionBenefitInputs.benefitValue"
            v-model:amtValue="visionBenefitInputs.amountValue"
            v-model:curValue="visionBenefitInputs.currencyValue"
            :label="visionBenefitInputs.label"
            :options="visionBenefitInputs.options"
          />

          <h2 class="text-[#114FF5] font-normal text-base mb-6 mt-[72px]">Dental Benefits</h2>
          <SelectInputField
            v-model:benValue="dentalBenefitInputs.benefitValue"
            v-model:amtValue="dentalBenefitInputs.amountValue"
            v-model:curValue="dentalBenefitInputs.currencyValue"
            :label="dentalBenefitInputs.label"
            :options="dentalBenefitInputs.options"
          />

          <h2 class="text-[#114FF5] font-normal text-base my-6">Pharmacy Benefits</h2>
          <div class="grid gap-6 mb-4">
            <SelectInputField
              v-for="(pharmacyBenefitInput, i) in pharmacyBenefitInputs"
              :key="i"
              v-model:benValue="pharmacyBenefitInput.benefitValue"
              v-model:amtValue="pharmacyBenefitInput.amountValue"
              v-model:curValue="pharmacyBenefitInput.currencyValue"
              :label="pharmacyBenefitInput.label"
              :options="pharmacyBenefitInput.options"
            />
          </div>
        </div>

        <div class="flex gap-6 justify-end mt-8">
          <button
            class="text-base font-bold leading-4 py-[10px] px-[22px] border border-[#080056] rounded-xl text-[#080056]"
          >
            Save as Draft
          </button>
          <button
            class="text-[#FFFFFF] font-bold leading-6 bg-[#FE4D3C] rounded-xl py-[10px] px-[54.5px]"
          >
            Save
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script lang="ts">
import ArrowLeft from './assets/arrow-left.vue'
import GreyInputField from './components/greyInputField.vue'
import GenericInputField from './components/genericInputField.vue'
import RadioInputField from './components/radioInputField.vue'
import SelectInputField from './components/selectInputField.vue'

export default {
  name: 'app',
  components: {
    GreyInputField,
    GenericInputField,
    RadioInputField,
    SelectInputField,
    ArrowLeft
  },
  data() {
    return {
      ownerInputs: [
        {
          label: 'Owner',
          value: '',
          type: 'text',
          placeholder: 'Autoloaded'
        },
        {
          label: 'Group Policy Number',
          value: '',
          type: 'text',
          placeholder: 'MTN - NG - CORPBILLACT - 0001'
        }
      ],
      descriptionInputs: [
        {
          label: 'Description',
          value: '',
          type: 'text',
          isOptional: true
        },
        {
          label: 'Est. Number of Employees',
          value: '',
          type: 'text',
          isOptional: false
        }
      ],
      billingPreference: {
        label: 'Billing Preference',
        value: ''
      },
      billingInputs: [
        {
          label: 'Name',
          value: '',
          type: 'text'
        },
        {
          label: 'Address',
          value: '',
          type: 'text'
        },
        {
          label: 'Email',
          value: '',
          type: 'email'
        },
        {
          label: 'Phone',
          value: '',
          type: 'tel'
        },
        {
          label: 'Plan',
          value: '',
          type: 'text'
        },
        {
          label: 'Coverage',
          value: '',
          type: 'text'
        }
      ],
      showDropDown: true,
      medicalBenefitInputs: {
        label: 'Medical Benefits',
        options: ['Goods', 'Health'],
        benefitValue: '',
        amountValue: null,
        currencyValue: ''
      },
      visionBenefitInputs: {
        label: 'Vision Benefits',
        options: ['Goods', 'Health'],
        benefitValue: '',
        amountValue: null,
        currencyValue: ''
      },
      dentalBenefitInputs: {
        label: 'Dental Benefits',
        options: ['Goods', 'Health'],
        benefitValue: '',
        amountValue: null,
        currencyValue: ''
      },
      pharmacyBenefitInputs: [
        {
          label: 'Generic Prescriptions',
          options: ['Goods', 'Health'],
          benefitValue: '',
          amountValue: null,
          currencyValue: ''
        },
        {
          label: 'Non-Generic (Specialty Brand Drugs) Prescriptions',
          options: ['Goods', 'Health'],
          benefitValue: '',
          amountValue: null,
          currencyValue: ''
        }
      ]
    }
  },
  methods: {
    handleSubmit() {
      const formData = {
        owner: this.ownerInputs[0].value,
        groupPolicyNumber: this.ownerInputs[1].value,
        description: this.descriptionInputs[0].value,
        numberOfEmployees: this.descriptionInputs[1].value,
        billingPreference: this.billingPreference.value
      }
      console.log(formData)

      this.ownerInputs[0].value = ''
      this.ownerInputs[1].value = ''
      this.descriptionInputs[0].value = ''
      this.descriptionInputs[1].value = ''
      this.billingPreference.value = ''
    }
  }
}
</script>
