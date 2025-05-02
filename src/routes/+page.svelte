<script >
    import { onMount } from 'svelte';
    import { NotebookPen, BriefcaseBusiness,Pickaxe,Mail } from '@lucide/svelte';
    import { draggable } from '@neodrag/svelte';
    import { properties } from "$lib/showBottom.svelte"

   
    function unlock( ){

    }
   

   

</script>
{#if properties.locked == true}

 <div id="lock-screen" class=" z-[3] w-full min-h-full  absolute flex flex-col justify-between items-center" use:draggable={{ axis: 'y',bounds: { bottom: 35}}} on:neodrag:end={()=> {properties.locked = false}}>   
    
    <div id="time-date" class="mt-[20%] flex flex-col items-center ">
        <h1 class="text-[51px]">1:45</h1>
        <p class="text-[12.8px]">Sat, 24 April</p>
    </div>
    <div id="swipe" class="mb-[10%]" >  
        <p class="text-[13px]">Swipe to unlock</p>
    </div>
   
</div>


{:else}
<div id="home-screen" class="z-[1] w-full h-full  ">
  
    <div id="apps-grid" class="w-full flex justify-start gap-5 p-4 pt-[50px] text-[white] flex-wrap">
        <a on:click={()=>{localStorage.setItem("locked", "true")}} href="/Apps/About" id="app" class="flex flex-col items-center justify-center ">
            <div id="app-icon"  class="p-[14px] bg-[#46766C]  rounded-[20px] flex items-center justify-center mb-[8px]">
                <NotebookPen size="22" color="white" />
            </div>
            <p class="text-[11.5px]">About me</p>
        </a>
        <a on:click={()=>{localStorage.setItem("locked", "true")}} href="/Apps/Projects" id="app" class="flex  flex-col items-center justify-center">
            <div id="app-icon"  class="p-[14px] bg-[#2A2A40]  rounded-[20px] flex items-center justify-center mb-[8px]">
                <Pickaxe size="22" color="white"/>
            </div>
            <p class="text-[11.5px]">projects</p>
        </a>
        <a on:click={()=>{localStorage.setItem("locked", "true")}} href="/Apps/Skills" id="app" class="flex flex-col items-center justify-center">
            <div id="app-icon"  class="p-[14px]  bg-[#201C13] rounded-[20px] flex items-center justify-center mb-[8px]">
                <Mail color="#F1B92E" />
            </div>
            <p class="text-[11.5px]">Skills</p>
        </a>
       

        
  

    </div>
    
  
</div>



{/if}