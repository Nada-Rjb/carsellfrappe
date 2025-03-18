<template>
  <section class="flow section" data-padding="compact">
    <div class="wrapper" id="main">
      <div class="invoice-actions">
        <!-- Dialog Component -->
        <Dialog
          v-model="dialog1"
          :options="{
            title: 'Invoice',
            size: 'md',
            closeButton: true,
            actions: [],
          }"
        >
          <div class="p-4">
            <div class="flex items-center justify-between">
              <img src="../../assets/imges/elfateh.jpg" class="w-6 h-6" alt="Company Logo" />
              <button @click="dialog1 = false" class="text-gray-500 hover:text-black">✕</button>
            </div>
            <h2 class="text-lg font-semibold mt-2">Invoice</h2>
            <p class="text-sm text-gray-600">ID: ACC-SINV-2025-00928</p>
            <p class="text-sm text-gray-600">Date: 13-03-2025</p>

            <hr class="my-2" />

            <div class="text-sm">
              <div class="flex justify-between py-1">
                <span>Item name with full name</span>
                <span>5 Kg</span>
                <span>1,850.0</span>
                <span>9,250.0</span>
              </div>
            </div>

            <hr class="my-2" />

            <p class="text-lg font-bold">Grand Total: <span class="text-black">{{ grandTotal }} EGP</span></p>

            <div class="flex justify-center mt-3 space-x-2">
              <button class="px-3 py-1 bg-gray-200 text-gray-600 rounded">1</button>
              <button class="px-3 py-1 bg-gray-200 text-gray-600 rounded">2</button>
              <button class="px-3 py-1 bg-gray-200 text-gray-600 rounded">...</button>
              <button class="px-3 py-1 bg-gray-200 text-gray-600 rounded">7</button>
            </div>
          </div>
        </Dialog>

        <button @click="dialog1 = true" class="mt-4 px-4 py-2 bg-blue-500 text-white rounded">Open Invoice</button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, inject } from "vue";
import { Dialog } from "frappe-ui";

const Emitter = inject("Emitter");

const dialog1 = ref(false);
const grandTotal = ref(9250.0); // تعريف grandTotal حتى لا تظهر أخطاء

onMounted(() => {
  console.log("Dialog should open on mount");
  dialog1.value = true;
  console.log("Dialog state:", dialog1.value);
});

if (Emitter) {
  console.log("Listening for 'open-quickview'");
  Emitter.on("open-quickview", () => {
    console.log("Received 'open-quickview' event!");
    dialog1.value = true;
  });
} else {
  console.error("Emitter is not available in child component!");
}
</script>

<style scoped>
/* إذا احتجت إلى تحسين الـ Dialog */
.dialog {
  border: 2px solid red; /* اختياري للتأكد من ظهور الـ Dialog */
}
</style>
