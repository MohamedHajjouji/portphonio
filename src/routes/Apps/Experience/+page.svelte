
<script>
    let experiences = [
        { title: "Mobile App Developer", description: "Developed scalable web applications and APIs." },
        { title: "Front-End Developer", description: "Designed user-friendly interfaces and improved user experiences." },
    ];
    let expandedIndex = null;

    function toggleDescription(index) {
        expandedIndex = expandedIndex === index ? null : index;
    }
</script>

<div class="p-6 pt-[100px] absolute bg-gradient-to-b from-[#536EB1] to-[#3A4A7D] h-full w-full flex flex-col gap-6 text-white rounded-t-[40px] rounded-b-[40px] shadow-2xl z-[1]">
    <h1 class="text-[28px] font-bold tracking-wide">Experiences</h1>
    <div class="space-y-6">
        {#each experiences as experience, index}
            <div class="bg-white text-gray-800 rounded-lg shadow-lg overflow-hidden transition-transform transform hover:scale-105">
                <div 
                    on:click={() => toggleDescription(index)} 
                    class="flex justify-between items-center p-4 cursor-pointer hover:bg-gray-100"
                >
                    <h2 class="text-[20px] font-semibold">{experience.title}</h2>
                    <button class="text-gray-500 hover:text-gray-700">
                        <svg
                            xmlns="http://www.w3.org/2000/svg"
                            class="h-6 w-6 transform transition-transform"
                            viewBox="0 0 20 20"
                            fill="currentColor"
                            class:rotate-180={expandedIndex === index}
                        >
                            <path fill-rule="evenodd" d="M5.23 7.21a.75.75 0 011.06.02L10 10.94l3.71-3.71a.75.75 0 111.06 1.06l-4 4a.75.75 0 01-1.06 0l-4-4a.75.75 0 01.02-1.06z" clip-rule="evenodd" />
                        </svg>
                    </button>
                </div>
                {#if expandedIndex === index}
                    <div class="p-4 bg-gray-50">
                        <p class="text-[16px] text-gray-700">{experience.description}</p>
                    </div>
                {/if}
            </div>
        {/each}
    </div>
</div>