<template>
    <LandingLayout :title="'Inicio'">
        <main class="selection:bg-primary">
            <!-- Seccion 1 -->
            <section class="lg:grid grid-cols-2 gap-12 items-center py-7 px-5 lg:py-20 lg:px-20">
                <div class="my-9 text-center lg:text-left lg:ml-14">
                    <h2 class="text-2xl md:text-3xl text-white font-bold mb-16">Mantenimiento experto y mudanza sin complicaciones, todo en un solo lugar</h2>
                    <PrimaryButton @click="goToWhatsApp">Contáctanos</PrimaryButton>
                </div>
                
                <el-carousel trigger="click" :height="carouselHeight">
                    <el-carousel-item v-for="item in groupImages1" :key="item">
                        <img :src="item" alt="">
                    </el-carousel-item>
                </el-carousel>
            </section>

            <!-- Seccion 2. Fletes y mudanzas -->
            <section>
                <h2 class="text-2xl font-bold text-white text-center mt-36 mb-8">NUESTROS SERVICIOS</h2>
                <article class="bg-[#292929] pt-8 pb-28 md:px-14 px-5 md:flex md:space-x-5 relative">
                    <div class="md:w-[40%] mb-9 md:mb-0">
                        <h3 class="text-xl text-white font-bold mb-10 mt-7">FLETES Y MUDANZAS</h3>
                        <p class="text-white text-lg">Ya sea que necesites trasladar muebles dentro de la ciudad o mudarte a otra región, nuestro equipo maneja cada detalle con precisión.</p>
                    </div>

                    <!-- carousel -->
                    <Carousel class="md:w-[60%]" v-bind="fletesMudanzasSettings" :breakpoints="breakpoints">
                        <Slide v-for="slide in groupImages2" :key="slide">
                            <img :src="slide" alt="">
                        </Slide>

                        <template #addons>
                            <Navigation />
                        </template>
                    </Carousel>

                    <!-- footer -->
                    <div class="absolute bottom-2 left-2">
                        <svg width="106" height="36" viewBox="0 0 106 36" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M66.9838 5.8904C76.3902 7.81014 81.4576 9.75287 89.6001 16.8356H77.4759V15.4383H85.1701C79.1546 9.91102 74.8704 8.32317 66.9838 5.8904ZM85.1701 18.2328C87.8718 18.0313 89.1867 18.1651 90.9991 18.9314L91.4654 21.726L104.989 25.2191V31.2739C105.108 27.4215 104.341 25.9099 100.325 25.2191L85.1701 22.1917V18.2328ZM82.8385 34.9999C90.7707 24.9756 94.4407 35.0381 94.4964 34.9999C94.5522 34.9617 92.114 22.9843 82.8385 34.9999ZM73.279 16.8356H74.4448V29.178H73.279V16.8356ZM63.4864 29.6437V1L1 1.69863L61.6211 2.63013V29.6437H63.4864ZM60.2222 7.05477V9.38353L1 8.45203L60.2222 7.05477ZM60.2222 16.8356V18.9314L1 18.2328L60.2222 16.8356ZM60.2222 26.3835V28.4794L1.23316 28.0136L60.2222 26.3835ZM15.9221 34.0684C24.1022 22.8017 27.462 35.6768 26.4142 34.0684C25.3665 32.46 23.0259 26.1058 15.9221 34.0684ZM1.46632 33.8355C7.42052 28.5991 9.96917 28.468 12.4248 34.0684C10.0001 26.4954 7.25771 27.8582 1.46632 33.8355Z" stroke="#9B9B9B" stroke-width="1.5"/>
                        </svg>
                        <p class="text-white italic mt-2">Nos aseguramos que cada objeto llegue a su destino de forma segura y a tiempo.</p>
                    </div>
                </article>
            </section>

            <!-- seccion 3. Mantenimiento y reparación -->
            <section class="mt-40 py-8 px-5 lg:mx-32">
                <article class="md:flex md:space-x-5">
                    <figure class="md:w-2/3">
                        <img src="@/../../public/images/Mantenimiento.png" alt="">
                    </figure>

                    <div class="md:w-1/3 mt-10 md:mt-0">
                        <h3 class="text-2xl font-bold text-white mb-10">MANTENIMIENTO Y SERVICIO TÉCNICO</h3>
                        <p class="text-white text-lg">Ofrecemos mantenimiento y servicio técnico especializado para una amplia gama de electrodomésticos, desde refrigeradores, lavadoras, hasta aires acondicionados y mucho más.</p>
                        <img class="mt-9" src="@/../../public/images/Mantenimiento_2.png" alt="">
                    </div>
                </article>

                <h2 class="text-2xl font-bold text-white mt-36 mb-10">SERVICIO DE REPARACIÓN PARA TODAS LAS MARCAS</h2>

                <!-- carousel -->
                <Carousel v-bind="branchesSettings" :breakpoints="BranchesBreakpoints">
                    <Slide v-for="slide in branchesImages" :key="slide">
                        <img class="w-1/3 md:w-[70%]" :src="slide" alt="">
                    </Slide>

                    <template #addons>
                        <Navigation />
                    </template>
                </Carousel>

                <div class="border-t border-[#5F5F5F] my-14"></div>
            </section>

            <!-- seccion 4. Rutas -->
            <section class="md:grid grid-cols-2 gap-3 py-20 px-5 lg:mx-32">
                <figure>
                    <img src="@/../../public/images/map.png" alt="">
                </figure>

                <div class="flex space-x-16 mt-9 md:mt-3">
                    <div class="text-right font-bold">
                        <h2 class="text-white text-4xl">Nuestras</h2>
                        <h3 class="text-primary text-4xl">rutas</h3>
                    </div>

                    <el-timeline style="max-width: 600px">
                        <el-timeline-item
                            v-for="activity in activities"
                            :key="activity"
                            >
                            <p class="text-white">{{ activity }}</p>
                        </el-timeline-item>
                    </el-timeline>
                </div>

                <div class="col-span-full border-t border-[#5F5F5F] my-14"></div>
            </section>


            <!-- sección 5. Formas de pago -->
            <section class="px-5 lg:mx-32 pb-14">
                <h2 class="text-white text-2xl text-center font-bold">Aceptamos las siguientes formas de pago</h2>
                <article class="flex space-x-12 justify-center mt-12">

                    <!-- efectivo -->
                    <div>
                        <p class="text-white text-lg">Efectivo</p>
                        <img class="w-20 mt-4 mx-auto" src="@/../../public/images/efectivo.png" alt="">
                    </div>

                    <!-- transferencia -->
                    <div>
                        <p class="text-white text-lg">Transferencia</p>
                        <img class="w-20 mx-auto" src="@/../../public/images/transferencia.png" alt="">
                    </div>

                    <!-- deposito -->
                    <div>
                        <p class="text-white text-lg">Deposito</p>
                        <img class="w-20 mx-auto" src="@/../../public/images/deposito.png" alt="">
                    </div>
                </article>
            </section>

            <!-- footer -->
            <Footer />  
        </main>
    </LandingLayout>
</template>

<script>
//general
import LandingLayout from '@/Layouts/LandingLayout.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import Footer from '@/Components/MyComponents/Landing/Footer.vue';

//imagenes
import Group1_1 from '@/../../public/images/Group1_1.png';
import Group1_2 from '@/../../public/images/Group1_2.png';
import Group1_3 from '@/../../public/images/Group1_3.png';
import Group1_4 from '@/../../public/images/Group1_4.png';
import Group2_1 from '@/../../public/images/Group2_1.png';
import Group2_2 from '@/../../public/images/Group2_2.png';
import Group2_3 from '@/../../public/images/Group2_3.png';
import Group2_4 from '@/../../public/images/Group2_4.png';
import whirpool from '@/../../public/images/whirpool.png';
import mabe from '@/../../public/images/mabe.png';
import samsung from '@/../../public/images/samsung.png';
import lg from '@/../../public/images/lg.png';
import daewoo from '@/../../public/images/daewoo.png';
import panasonic from '@/../../public/images/panasonic.png';
import bosch from '@/../../public/images/bosch.png';

//carousel
import { Carousel, Navigation, Pagination, Slide } from 'vue3-carousel';
import 'vue3-carousel/dist/carousel.css';

export default {
data() {
    
    return {
        carouselHeight: '500px', //tamaño del carusel de elemen plus
        groupImages1: [
            Group1_1,
            Group1_2,
            Group1_3,
            Group1_4
        ],
        groupImages2: [
            Group2_1,
            Group2_2,
            Group2_3,
            Group2_4
        ],
        branchesImages: [
            panasonic,
            whirpool,
            samsung,
            daewoo,
            bosch,
            mabe,
            lg,
        ],
        fletesMudanzasSettings: {
            wrapAround: true,
            itemsToShow: 2,
            snapAlign: 'start',
            autoplay: 4000,
        },
        branchesSettings: {
            wrapAround: true,
            itemsToShow: 5,
            snapAlign: 'start',
            autoplay: 4000,
        },
        breakpoints: {
            // 320px and up
            320: {
                itemsToShow: 1,
                snapAlign: 'start',
            },
            // 700px and up
            700: {
                itemsToShow: 1.25,
                snapAlign: 'start',
            },
            // 1024 and up
            1024: {
                itemsToShow: 2,
                snapAlign: 'start',
            },
        },
        BranchesBreakpoints: {
            // 320px and up
            320: {
                itemsToShow: 2,
                snapAlign: 'start',
            },
            // 700px and up
            700: {
                itemsToShow: 3,
                snapAlign: 'start',
            },
            // 1024 and up
            1024: {
                itemsToShow: 5,
                snapAlign: 'start',
            },
        },
        activities: [
            'Guadalajara',
            'Tlajomulco',
            'Tonalá',
            'Chapala',
            'Tepic',
            'Sinaloa',
            'Mazatlán',
        ]
    }
},
components:{
    LandingLayout,
    PrimaryButton,
    Navigation,
    Pagination,
    Carousel,
    Footer,
    Slide,
},
props:{

},
methods:{
    goToWhatsApp() {
      const url = "https://api.whatsapp.com/send?phone=523314179923&text=Hola!%20vi%20tu%20página%20de%20fletes%20y%20reparaciones.%20Me%20interesa%20su%20servicio!";
      window.open(url, "_blank", "noopener,noreferrer");
    },
    updateCarouselHeight() {
      const width = window.innerWidth;
      if (width < 430) {
        this.carouselHeight = '300px';
        this.galeryCarouselHeight = '300px';
      } else if (width >= 430 && width < 1024) {
        this.carouselHeight = '480px';
        this.galeryCarouselHeight = '430px';
      } else if (width >= 1024 && width < 1350) {
        this.carouselHeight = '330px';
      } else {
        this.carouselHeight = '500px';
      }
    },
},
mounted() {
    this.updateCarouselHeight();
    window.addEventListener('resize', this.updateCarouselHeight);
},
beforeUnmount() {
    window.removeEventListener('resize', this.updateCarouselHeight);
},
}
</script>

<style>
.el-carousel__item h3 {
  color: transparent;
  opacity: 0.75;
  line-height: 150px;
  margin: 0;
  text-align: center;
}

.el-carousel__item:nth-child(2n) {
  background-color: transparent;
}

.el-carousel__item:nth-child(2n + 1) {
  background-color: transparent;
}

.el-carousel__arrow {
    background-color: rgba(99, 98, 98, 0.562);
    /* Fondo semitransparente */
    border-radius: 50%;
    /* Bordes redondeados */
    color: white;
    /* Color del icono */
}

.el-carousel__arrow--left {
    left: 10px;
    /* Ajusta la posición de la flecha izquierda */
}

.el-carousel__arrow--right {
    right: 10px;
    /* Ajusta la posición de la flecha derecha */
}

/* Puedes agregar más estilos personalizados aquí */
.el-carousel__arrow:hover {
    background-color: rgba(131, 130, 130, 0.562);
    /* Cambia el fondo al hacer hover */
    /* transform: scale(1.1); Efecto de escalado al hacer hover */
}
</style>