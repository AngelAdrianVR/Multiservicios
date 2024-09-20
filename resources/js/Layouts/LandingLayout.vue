<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import { Head, Link, router  } from '@inertiajs/vue3';
import ApplicationMark from '@/Components/ApplicationMark.vue';
import Banner from '@/Components/Banner.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';

defineProps({
    title: String,
});

// Variables reactivas
const isNavbarFixed = ref(true);
const lastScrollY = ref(0);

const showingNavigationDropdown = ref(false);

// Función para manejar el scroll
const handleScroll = () => {
  const currentScrollY = window.scrollY;

  if (currentScrollY > lastScrollY.value && currentScrollY > window.innerHeight) {
    // Si se hace scroll hacia abajo y se ha pasado el alto de la pantalla
    isNavbarFixed.value = false;
  } else {
    // Si se hace scroll hacia arriba
    isNavbarFixed.value = true;
  }

  lastScrollY.value = currentScrollY;
};

// Ciclos de vida del componente
onMounted(() => {
  window.addEventListener('scroll', handleScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll);
});

const switchToTeam = (team) => {
    router.put(route('current-team.update'), {
        team_id: team.id,
    }, {
        preserveState: false,
    });
};

const logout = () => {
    router.post(route('logout'));
};

const goToWhatsApp = () => {
  const url = "https://api.whatsapp.com/send?phone=523313825055&text=Hola!%20vi%20tu%20página%20de%20fletes%20y%20reparaciones.%20Me%20interesa%20su%20servicio!";
  window.open(url, "_blank", "noopener,noreferrer");
};
</script>

<style>
/* Estilos para la barra de navegación */
.navbar {
    position: absolute;
    top: 0;
    background-color: #343434;
    opacity: 0.9;
}
.fixed-navbar {
    position: fixed;
    width: 100%;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    z-index: 100;
}
html {
    scroll-behavior: smooth;
}
.custom-style .el-segmented {
  --el-segmented-bg-color: #818181;
  --el-segmented-color: #000;
  --el-segmented-item-selected-color: #FFFFFF;
  --el-segmented-item-selected-bg-color: #a1a1a1;
  --el-border-radius-base: 16px;
}
</style>

<template>
    <div>
        <Head :title="title" />

        <Banner />

        <div class="min-h-screen bg-[#343434]">
            <nav :class="['navbar', { 'fixed-navbar': isNavbarFixed }]" class="bg-[#343434] py-1 px-9">
                <!-- Primary Navigation Menu -->
                <div class="max-w-full px-4 sm:px-6 lg:px-8">
                    <div class="flex justify-between h-16">
                        <div class="flex justify-between w-full mr-16">
                            <!-- Logo -->
                            <div class="shrink-0 flex items-center">
                                <Link :href="route('home')">
                                    <ApplicationMark class="block h-12 w-auto" />
                                </Link>
                            </div>

                            <!-- Navigation Links -->
                            <div class="hidden space-x-10 sm:-my-px sm:ms-10 sm:flex">
                                <NavLink :href="route('home')" :active="route().current('home')">
                                    Inicio
                                </NavLink>
                                <NavLink :href="route('services')" :active="route().current('services')">
                                    Servicios
                                </NavLink>
                                <button @click="goToWhatsApp" class="text-gray-400 hover:text-white">
                                    <i class="fa-brands fa-whatsapp"></i>
                                </button>

                            </div>
                        </div>

                        <!-- Hamburger -->
                        <div class="-me-2 flex items-center sm:hidden">
                            <button class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 focus:text-gray-500 transition duration-150 ease-in-out" @click="showingNavigationDropdown = ! showingNavigationDropdown">
                                <svg
                                    class="h-6 w-6"
                                    stroke="currentColor"
                                    fill="none"
                                    viewBox="0 0 24 24"
                                >
                                    <path
                                        :class="{'hidden': showingNavigationDropdown, 'inline-flex': ! showingNavigationDropdown }"
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                        stroke-width="2"
                                        d="M4 6h16M4 12h16M4 18h16"
                                    />
                                    <path
                                        :class="{'hidden': ! showingNavigationDropdown, 'inline-flex': showingNavigationDropdown }"
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                        stroke-width="2"
                                        d="M6 18L18 6M6 6l12 12"
                                    />
                                </svg>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Responsive Navigation Menu -->
                <div :class="{'block': showingNavigationDropdown, 'hidden': ! showingNavigationDropdown}" class="sm:hidden">
                    <div class="pt-2 pb-3 space-y-1">
                        <ResponsiveNavLink :href="route('home')" :active="route().current('home')">
                            Inicio
                        </ResponsiveNavLink>
                        <ResponsiveNavLink :href="route('services')" :active="route().current('services')">
                            Servicios
                        </ResponsiveNavLink>
                    </div>
                </div>
            </nav>

            <!-- Page Heading -->
            <header v-if="$slots.header" class="bg-white shadow">
                <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
                    <slot name="header" />
                </div>
            </header>

            <!-- Page Content -->
            <main>
                <slot />
            </main>
        </div>
    </div>
</template>
