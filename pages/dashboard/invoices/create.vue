<template>
  <main  class="px-4 sm:px-6 lg:px-8">
    <div class="container p-4 max-w-xl bg-white rounded-xl border">
     <div>
     <div class="mb-6">
      <h1 class="text-2xl font-bold ">Generate Invoice</h1>
      <p class="text-sm text-gray-300">Please fill the form with details regarding the import or export to initiate an invoice</p>
     </div>
     </div>
      <form @submit.prevent="generateInvoice">
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Invoice Number</label>
          <input v-model="invoiceForm.invoiceNumber" type="text"  class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Item Name</label>
          <input v-model="invoiceForm.itemName" type="text"  class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Quantity</label>
          <input v-model="invoiceForm.quantity" type="number"  class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Type (Import/Export)</label>
          <select v-model="invoiceForm.type"  class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6">
            <option>Import</option>
            <option>Export</option>
          </select>
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Weight (kg)</label>
          <input v-model="invoiceForm.weight" type="number"  class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Cost</label>
          <input v-model="invoiceForm.cost" type="number"  class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Sender Name</label>
          <input v-model="invoiceForm.senderName" type="text"  class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Receiver Name</label>
          <input v-model="invoiceForm.receiverName" type="text"  class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
        </div>
        <div class="mb-4">
          <label class="block text-sm font-medium text-gray-700">Date</label>
          <input v-model="invoiceForm.date" type="date"  class="mt-1 block w-full rounded-t-md outline-none border-[#DBC3DD] border py-4 pl-4 shadow-sm placeholder:text-gray-400 sm:text-sm sm:leading-6" />
        </div>
        <div class="w-full pt-6">
          <button type="submit" class="bg-black text-white px-4 py-3  rounded w-full">Submit</button>
        </div>
      </form>
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const invoiceForm = ref({
  invoiceNumber: '',
  itemName: '',
  quantity: 0,
  type: 'Import',
  weight: 0,
  cost: 0,
  senderName: '',
  receiverName: '',
  date: ''
})

const generateInvoice = () => {
  // Handle invoice generation logic here
  console.log(invoiceForm.value)
}

definePageMeta({
    layout: 'dashboard'
})
</script>
