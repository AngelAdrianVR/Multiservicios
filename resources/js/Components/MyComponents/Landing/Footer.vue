<template>
    <footer class="bg-[#292929] px-7 pt-4 pb-24  flex items-center justify-between w-full relative">
        <ApplicationMark class="block h-7 md:h-9 lg:h-12 w-auto" />

        <!-- logo dtw -->
        <a href="https://app.dtw.com.mx/" target="_blank" class="flex items-center space-x-3 text-white">
            <p>By</p>
            <img class="w-12 md:w-16 lg:w-20" src="@/../../public/images/dtw_white_logo.png" alt="">
        </a>

        <div class="text-xs flex items-center space-x-3 text-white absolute left-2 bottom-14">
            <p>Copyright</p>
            <p>Mantenimiento y mudanza 2024. Todos los derechos reservados.</p>
        </div>

        <div class="text-xs flex items-center space-x-3 text-white absolute left-2 bottom-1">
            <div>
                <p>33 13 82 50 55</p>
                <p>33 14 17 99 23</p>
                <p>33 34 08 98 59</p>
            </div>
            <button class="text-gray-400 hover:text-white">
                <i class="fa-brands fa-whatsapp"></i>
            </button>
        </div>
    </footer> 
</template>

<script>
import ApplicationMark from '@/Components/ApplicationMark.vue';

export default {
components: {
    ApplicationMark
}
}
</script>
