<template>
  <section class="flow section" data-padding="compact">
    <div class="wrapper" id="main">
      <div class="invoice-actions">
        <!-- Dialog Component -->
        <Button @click="dialog = true">
  Show Dialog
</Button>
<Dialog v-model="dialog1">
  <template #body-title >
    <div class="flex justify-center items-center w-full gap-[10.5rem]">
      <img src="../../assets/imges/elfateh.jpg" class="w-7 h-7" alt="Company Logo" />
    <h2 class="text-lg font-semibold ">Invoice</h2>
</div>
  </template>
  <template #body-content>
         <!-- Invoice Details -->
              <p class="text-xl text-black">ID: ACC-SINV-2025-00928</p>
              <p class="text-xl text-black mt-4" > Date: 13-03-2025</p>  
              <hr class="my-3 border-[#D9D9D9] border-[1px] " />
          <!-- Invoice Items -->
          <div class="text-xl text-black p-2">
                <div class=" py-1">
                  <span>Item name with full name</span>
                  <div class="flex gap-10 mt-5">
                    <span>5<span class="ml-1">kg</span></span>
                    <span>1,850.0</span>
                  <span>9,250.0</span>
                  </div>
                </div>
                <div class=" py-1">
                  <span>Item name with full name</span>
                  <div class="flex gap-10 mt-5">
                    <span>5<span class="ml-1">kg</span></span>
                    <span>1,850.0</span>
                  <span>9,250.0</span>
                  </div>
                </div>
                <div class=" py-1">
                  <span>Item name with full name</span>
                  <div class="flex gap-10 mt-5">
                    <span>5<span class="ml-1">kg</span></span>
                    <span>1,850.0</span>
                  <span>9,250.0</span>
                  </div>
                </div>
              </div>
              <hr class="my-3 border-[#D9D9D9] border-[1px] " />
   <!-- Grand Total -->
              <p class="text-lg font-bold ">
                Grand Total: <span class="text-black">1421 EGP</span>
              </p>
              </template>
  <template #actions>
    <Button variant="solid">
      Confirm
    </Button>
    <Button
      class="ml-2"
      @click="dialog1 = false"
    >
      Close
    </Button>
  </template>
</Dialog>
        <!-- Open Invoice Button -->
        <button @click="openDialog" class="mt-4 px-5 py-2 bg-blue-600 text-white font-bold rounded-md">
          Open Invoice
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, inject } from "vue";
import { Dialog } from "frappe-ui";

const Emitter = inject("Emitter");
const dialog1 = ref(false);
const grandTotal = ref(9250.0); // Default total

// Open Dialog Function
const openDialog = () => {
  console.log("Opening Invoice Dialog...");
  dialog1.value = true;
};

// Check if the component is mounted
onMounted(() => {
  console.log("Invoice Component Mounted");
  openDialog(); // Open dialog on mount
});

// Event Listener for 'open-quickview'
if (Emitter) {
  console.log("Listening for 'open-quickview' event...");
  Emitter.on("open-quickview", () => {
    console.log("Received 'open-quickview' event!");
    dialog1.value = true;
  });
} else {
  console.error("Emitter is not available in child component!");
}
</script>

<style scoped>

/* Ensure Dialog Content is Visible */
:deep(.frappe-dialog) {
  display: block !important;
  z-index: 9999 !important;
  opacity: 1 !important;
  visibility: visible !important;
}

/* Debugging: Ensure Dialog Elements are Visible */
.bg-white {
  background-color: white !important;
  color: black !important;
}

dialog {
  border: 2px solid red; /* For debugging, remove later */
}
</style>
