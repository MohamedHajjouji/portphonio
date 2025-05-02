<script >

let {children} = $props()
    
    import { onMount } from 'svelte';
    import "../app.css";
    import { WifiHigh,BatteryLow,ChevronLeft, Square,AlignJustify } from '@lucide/svelte';
    import { properties } from "$lib/showBottom.svelte"
    let isMobile = $state(false);
   
    onMount(() => {
  console.log('Mounted. Width:', window.innerWidth); // <-- debug
  isMobile = window.innerWidth <= 768;
  console.log('Resized. isMobile:', isMobile); 

  window.addEventListener('resize', () => {
    isMobile = window.innerWidth <= 768;
    console.log('Resized. isMobile:', isMobile); // <-- debug
  });
});

    

</script>

{#if isMobile}
<div id="phone-content " class="'w-screen h-screen flex flex-col items-center justify-center " >
    {@render children()}
    <img src="/bg.png"  class="absolute w-full h-full z-[0]" alt="">
</div>
    
{:else}
<div class="w-full h-screen flex items-center justify-center bg-[#1E1E1E] text-white  " >
   
    <div id="phone-screen"  class="w-[320px] h-[764px] max-h-[80dvh]  border-[5px] border-[#282828]  rounded-[45px] shadow-2xl flex flex-col items-center justify-betweeen relative overflow-hidden">
        <div id="status-bar " class="flex-row w-full  flex pt-[5px] justify-between px-6 rounded-t-3xl  z-10 absolute">
            <div>
            <span id="time" class="text-[11px]">23:19</span>
            </div>
            <div class="flex gap-2 items-center justify-center">
                <div class="mb-[5px]">
                <WifiHigh size="15"/>
                </div>
                <span id="battery" class="text-[12px]">12%</span>
                <BatteryLow size="17" />
            </div>
        </div>
     
            {@render children()}
       
      
            
     {#if properties.locked == false}
       <div id="bottom-bar" class="flex   z-[1] w-full justify-around py-[20px]">
      
        <AlignJustify size="18"/>
      
      <a href="/" on:click={ ()=> {localStorage.setItem("locked", "false")}}>
        <Square size="18"/>
      </a>
      
      <a href="/" on:click={ ()=> {localStorage.setItem("locked", "false")}}>
        <ChevronLeft size="18"/>
      </a>
      </div>
      {/if}
    
        


        <img src="/bg.png"  class="absolute w-full h-full z-[0]" alt="">
    </div>

</div>
    
{/if}

