<template>
<div  id="main">        <!-- Dialog Component -->     
        <Dialog  
  v-model="dialog1"  
  class="dialog-fullscreen"
  :style="{  
    width: '100vw',
    height: '100%',
    display: 'flex',
    alignItems: 'center',
    justifyContent: 'center',
    background: 'white'
  }"
>



>

  <template #body-title >
    <div class="flex justify-center items-center w-full gap-[10.5rem] mt-0">
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
          <div class=" max-h-[250px] overflow-y-auto text-xl text-black p-2">
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
  
</Dialog></div>
        <!-- Open Invoice Button -->
    
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

<style scoped
 >
html, body {
  height: 100vh;
  overflow: hidden !important; /* يمنع أي تمرير غير مرغوب */
  margin: 0;
  padding: 0;
  width: 100%;
}

/* Fix Dialog Appearance */
.dialog-fullscreen {
  position: fixed !important;
  top: 0;
  left: 0;
  width: 100vw !important;
  height: 100vh !important;
  max-width: 100vw !important;
  max-height: 100vh !important;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: white !important;
  overflow: hidden !important;
}

* {
  box-sizing: border-box;
  max-width: 100vw !important;
  overflow-x: hidden !important;
}


.wrapper .dialog-class {
  margin: 0 !important;
  padding: 0 !important;
  width: 100% !important;
  height: 100% !important;
  display: flex;
  align-items: center;
  justify-content: center;
}

* {
  margin: 0 !important;
  padding: 0 !important;
  outline: 1px solid red !important; /* رؤية الحواف */
}

/* Ensure Dialog Content is Visible */
/* back groud  */
#headlessui-dialog-2{
  background-color: brown;
  margin: '0' !important

}
#headlessui-dialog-panel-5
{
  margin: 0 !important;
border: solid red  !important;
border-radius: 10px;
}
#headlessui-dialog-panel-17{
  margin: 0!important;
}
</style>
