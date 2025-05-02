<script>
    import { onMount } from 'svelte';
    import Swiper from 'swiper';
    import 'swiper/css';
    import { Navigation, Pagination } from 'swiper/modules';
  
    const projects = [
      {
        title: "Project 1",
        description: "This is the first project. it was made by me in 2025, and it took me around x amount of time ",
        images: ["image1", "image2"],
        link: "/projects/project1"
      },
      {
        title: "Project 2",
        description: "This is the second project.",
        images: ["image1", "image2", "image3", "image4"],
        link: "/projects/project2"
      },
      {
        title: "Project 3",
        description: "This is the third project.",
        images: ["image1", "image2"],
        link: "/projects/project3"
      }
    ];
  
    let currentProject = 0;
    let swiperInstance;
    let swiperReady = false;
  
    // Initialize or reinitialize Swiper
    function initSwiper() {
      if (swiperInstance) {
        swiperInstance.destroy(true, true); // Destroy with cleanup
      }
      
      swiperInstance = new Swiper('.swiper-container', {
        modules: [Navigation, Pagination],
        direction: 'horizontal',
        loop: false, // Disable loop for dynamic slides
        pagination: {
          el: '.swiper-pagination',
          clickable: true
        },
        on: {
          init: () => swiperReady = true
        }
      });
    }
  
    onMount(() => {
      initSwiper();
      return () => swiperInstance?.destroy(); // Cleanup on component unmount
    });
  
    function nextProject() {
      currentProject = (currentProject + 1) % projects.length;
      // Wait for DOM update before reinitializing
      setTimeout(initSwiper, 10);
    }
  
    function prevProject() {
      currentProject = (currentProject - 1 + projects.length) % projects.length;
      setTimeout(initSwiper, 10);
    }
  </script>
  <div class="w-full h-full bg-[#0F172A] z-[1] absolute"> 
  <div class="swiper-container  w-full bg-[#0F172A]" key={currentProject}>
    <div class="swiper-wrapper">
      {#each projects[currentProject].images as image, index}
        <div class="swiper-slide w-full">{image} {index + 1}</div>
      {/each}
    </div>
    <div class="swiper-pagination"></div>
  </div>

  <div class="text-white px-3 gap-[10px]  h-[25%] justify-between flex flex-col w-full">
    
    <div>
      <h1 class="text-[18px] font-semibold">{projects[currentProject].title}</h1>
      <p class="text-[12px] text-[#94A3B8]">personal</p>
    </div>

    <p class="text-[12px] text-white">{projects[currentProject].description}</p>

    <a
      class="text-[12px] underline text-[#6366F1] transition"
      href={projects[currentProject].link}
      target="_blank"
    >
      see project live
    </a>

    <div class="flex gap-4 mt-3">
      <button
        on:click={prevProject}
        class="flex-1 text-[12px] bg-[#6366F1] text-[#fff] py-2 rounded-md hover:bg-[#4F46E5] transition font-medium"
      >
        Previous Project
      </button>
      <button
        on:click={nextProject}
        class="flex-1 text-[12px] bg-[#6366F1] text-[#fff] py-2 rounded-md hover:bg-[#4F46E5] transition font-medium"
      >
        Next Project
      </button>
    </div>
  </div>
</div>

  <style>
    .swiper-container {
      width: 100%;
      height: 60%;
      margin-bottom: 20px;
    }
    .swiper-slide {
      display: flex;
      justify-content: center;
      align-items: center;
      background: #f5f5f5;
      border: 1px solid #ddd;
    }
    .swiper-pagination {
      position: relative;
      margin-top: 10px;
    }
  </style>