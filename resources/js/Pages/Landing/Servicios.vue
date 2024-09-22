<template>
    <LandingLayout :title="'Servicios'">
        <!-- sección 1 introduccion -->
        <section class="py-32 px-5 lg:mx-32">
          <div class="flex justify-between items-center">
            <h2 class="text-2xl text-white font-bold">SERVICIO DE FLETES Y MUDANZAS GIL</h2>
            <img src="@/../../public/images/logoGil.png" alt="">
          </div>

          <p class="text-lg text-white mt-2">Ya sea que necesites trasladar muebles dentro de la ciudad o mudarte a otra región, nuestro equipo maneja cada detalle con precisión.</p>

          <div class="mt-12 grid md:grid-cols-2 lg:grid-cols-4 gap-7">
            <div v-for="card in serviceCards" :key="card" class="border border-white rounded-xl py-4 px-7 text-center">
              <p class="text-white mb-7 text-lg">{{ card.label }}</p>
              <span v-html="card.icon"></span>
              <p class="text-[#979797] mt-7">{{ card.description }}</p>
            </div>
          </div>

          <div class="mt-20">
              <svg width="106" height="36" viewBox="0 0 106 36" fill="none" xmlns="http://www.w3.org/2000/svg">
                  <path d="M66.9838 5.8904C76.3902 7.81014 81.4576 9.75287 89.6001 16.8356H77.4759V15.4383H85.1701C79.1546 9.91102 74.8704 8.32317 66.9838 5.8904ZM85.1701 18.2328C87.8718 18.0313 89.1867 18.1651 90.9991 18.9314L91.4654 21.726L104.989 25.2191V31.2739C105.108 27.4215 104.341 25.9099 100.325 25.2191L85.1701 22.1917V18.2328ZM82.8385 34.9999C90.7707 24.9756 94.4407 35.0381 94.4964 34.9999C94.5522 34.9617 92.114 22.9843 82.8385 34.9999ZM73.279 16.8356H74.4448V29.178H73.279V16.8356ZM63.4864 29.6437V1L1 1.69863L61.6211 2.63013V29.6437H63.4864ZM60.2222 7.05477V9.38353L1 8.45203L60.2222 7.05477ZM60.2222 16.8356V18.9314L1 18.2328L60.2222 16.8356ZM60.2222 26.3835V28.4794L1.23316 28.0136L60.2222 26.3835ZM15.9221 34.0684C24.1022 22.8017 27.462 35.6768 26.4142 34.0684C25.3665 32.46 23.0259 26.1058 15.9221 34.0684ZM1.46632 33.8355C7.42052 28.5991 9.96917 28.468 12.4248 34.0684C10.0001 26.4954 7.25771 27.8582 1.46632 33.8355Z" stroke="#9B9B9B" stroke-width="1.5"/>
              </svg>
              <p class="text-white italic mt-2">Transformamos cada mudanza en una experiencia confiable y sin complicaciones.</p>
          </div>
        </section>

        <!-- sección 2 Mantenimiento y servicio tecnico -->
        <section class="py-10 px-5 lg:mx-32">
          <h2 class="text-2xl text-center text-white font-bold">MANTENIMIENTO Y SERVICIO TECNICO</h2>
          <p class="text-lg text-white mt-9">
            Ofrecemos reparación, mantenimiento e instalación de electrodomésticos de línea blanca y aires acondicionados.
            Ya sea que necesites optimizar el rendimiento de tu refrigerador, lavadora, secadora, o instalar y reparar tu aire acondicionado, 
            nuestro equipo de técnicos especializados te brinda un servicio rápido, confiable y de calidad.
          </p>

          <img class="mt-16" src="@/../../public/images/mantenimiento_3.png" alt="">

          <div class="text-center">
            <PrimaryButton class="!px-16" @click="goToWhatsApp">Contáctanos</PrimaryButton>
          </div>
        </section>

        <!-- sección 3. Galería de trabajos -->
        <section class="py-24 px-5 lg:mx-32">
          <div class="border-t border-[#5F5F5F] my-14"></div>
            <h2 class="text-2xl text-center font-bold text-white mb-7">GALERÍA DE TRABAJOS</h2>
            <p class="text-white text-lg text-center mb-12">Contamos con más de 5 años de experiencia</p>

            <div>
                <el-carousel :interval="3000" type="card" :height="galeryCarouselHeight">
                    <el-carousel-item v-for="item in galery" :key="item">
                        <figure class="md:w-[80%] w-[89%] mx-auto">
                            <img class="mx-auto mt-4 object-contain" :src="item" alt="">
                        </figure>
                    </el-carousel-item>
                </el-carousel>
            </div>
        </section>

        <!-- sección 4 Estadisticas de trabajos -->
        <section class="grid md:grid-cols-3 grid-cols-2 gap-7 py-20 px-5 lg:mx-32">
            <StatisticCard v-for="item in statistics" :key="item" :label="item.label" :value="item.value" />
        </section>

        <!-- footer -->
        <Footer /> 
    </LandingLayout>
</template>

<script>
//general
import LandingLayout from '@/Layouts/LandingLayout.vue';
import StatisticCard from '@/Components/MyComponents/Landing/StatisticCard.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import Footer from '@/Components/MyComponents/Landing/Footer.vue';

//imagenes
import galery_1 from '@/../../public/images/galery_1.png';
import galery_2 from '@/../../public/images/galery_2.png';
import galery_3 from '@/../../public/images/galery_3.png';
import galery_4 from '@/../../public/images/galery_4.png';
import galery_5 from '@/../../public/images/galery_5.png';
import galery_6 from '@/../../public/images/galery_6.png';
import galery_7 from '@/../../public/images/galery_7.png';
import galery_8 from '@/../../public/images/galery_8.png';

export default {
data() {
    return {
        galeryCarouselHeight: '450px', //tamaño del carusel de elemen plus
        serviceCards: [
          {
            label: 'Fletes',
            icon: '<svg class="mx-auto" width="153" height="109" viewBox="0 0 153 109" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M12.497 2.91837H94.3101L93.671 59.1905H23.3628V61.1088H93.671V67.5034H96.2276V1H94.3101H10.5795C6.43511 2.10083 4.75278 3.57531 2.9095 7.39456C2.9095 7.39456 3.3133 79.4732 3.54867 80.2925C3.78404 81.1118 10.0429 85.7679 9.94032 86.6871C9.83774 87.6063 2.47237 86.6871 1.63117 86.6871C0.789974 86.6871 0.789244 95 1.63117 95H14.4145C13.7753 80.932 38.7028 70.7007 47.0119 88.6054L98.1451 87.966V93.7211H105.176C103.898 80.2925 122.433 66.2245 137.773 81.5714H148C148 81.5714 147.159 56.3929 146.722 55.3537C146.285 54.3146 133.938 28.4966 132.66 26.5782C131.382 24.6599 100.702 25.9388 100.702 25.9388V73.2585H4.827V8.67347C7.22949 5.42721 8.73741 4.08597 12.497 2.91837Z" fill="white" stroke="white"/><path d="M108 57.6175V34.3825C108 34.3825 127.49 33.5219 128.522 34.3825C129.555 35.243 142.405 56.7568 141.99 57.6175C141.576 58.4781 108 57.6175 108 57.6175Z" fill="#343434"/><circle cx="124" cy="95" r="13" fill="#FCFCFC"/><path d="M152 86.5741C152 85.2824 140.029 86.5741 139.174 86.5741C138.319 86.5741 140.884 94.3242 141.199 95.185C141.514 96.0458 152 96.4764 152 95.185V86.5741Z" fill="white" stroke="white"/><circle cx="124" cy="95" r="6" fill="#343434"/><circle cx="32" cy="96" r="13" fill="white"/><circle cx="32" cy="96" r="6" fill="#343434"/></svg>',
            description: 'Servicio de traslado de objetos y mercancías.',
          },
          {
            label: 'Mudanzas residenciales',
            icon: '<svg class="mx-auto" width="124" height="97" viewBox="0 0 124 97" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M10.5 37.5V96H49M113.5 37.5C113.5 60.3457 113.5 73.1543 113.5 96H76M49 96V44H76V96M49 96H76M123 44C100.74 28.7696 84.2599 17.2304 62 2L1 44" stroke="white" stroke-width="2"/></svg>',
            description: 'Aseguramos tus pertenencias.',
          },
          {
            label: 'Mudanzas empresariales',
            icon: '<svg class="mx-auto" width="106" height="109" viewBox="0 0 106 109" fill="none" xmlns="http://www.w3.org/2000/svg"><g filter="url(#filter0_d_13558_102)"><path d="M5 25.3582L28.6418 1H101M5 25.3582H76.6418M5 25.3582V99.1493H76.6418M101 1L76.6418 25.3582M101 1V76.2239L76.6418 99.1493M76.6418 25.3582V99.1493" stroke="white" stroke-width="2"/><path d="M34.3743 60.4627L29.3594 64.7612V26.0746L53.0012 1H75.9265L51.5683 26.0746V64.7612L45.837 60.4627L40.1056 64.7612L34.3743 60.4627Z" fill="white" stroke="white"/></g><defs><filter id="filter0_d_13558_102" x="0" y="0" width="106" height="108.149" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB"><feFlood flood-opacity="0" result="BackgroundImageFix"/><feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/><feOffset dy="4"/><feGaussianBlur stdDeviation="2"/><feComposite in2="hardAlpha" operator="out"/><feColorMatrix type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.25 0"/><feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_13558_102"/><feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_13558_102" result="shape"/></filter></defs></svg>',
            description: 'Tu negocio en movimiento sin contratiempos.',
          },
          {
            label: 'Servicio de maniobras',
            icon: '<svg class="mx-auto" width="104" height="107" viewBox="0 0 104 107" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M1 1C1 1 18.7677 3.63226 21.4 6.26452C22.4912 7.35567 27.3139 19.1894 32.5871 32.6719M32.5871 32.6719L26.6645 50.3548L33.2452 66.8065M32.5871 32.6719C36.3711 42.347 40.3871 52.8711 43.4224 60.8839M33.2452 66.8065L39.8258 83.2581C41.6934 79.6527 43.1425 77.6333 48.3806 74.0452C48.3806 74.0452 46.3611 68.6415 43.4224 60.8839M33.2452 66.8065L43.4224 60.8839M70.7548 85.2323C83.3474 79.5785 90.4075 76.4086 103 70.7548M49.6968 42.2549L43.4224 45.0903L56.9355 74.7032C60.7585 74.7469 62.7595 75.3888 66.1484 79.3097L97.0774 64.8323L81.2839 27.9806L77.9936 29.4675M49.6968 42.2549L37.1935 14.1613L64.8323 2.31613L77.9936 29.4675M49.6968 42.2549L77.9936 29.4675" stroke="white"/><circle cx="54.303" cy="89.8392" r="7.89677" fill="white"/><circle cx="54.3011" cy="89.8382" r="16.1097" stroke="white" stroke-width="2"/><rect x="56.3242" y="5.73633" width="9.2129" height="10.8105" transform="rotate(65.7947 56.3242 5.73633)" fill="white"/><rect x="69.1289" y="33.5332" width="12.8147" height="15.2844" transform="rotate(64.1746 69.1289 33.5332)" fill="white"/></svg>',
            description: 'Manejo seguro y eficiente de carga y descarga.',
          },
        ],
        galery: [
            galery_1,
            galery_2,
            galery_3,
            galery_4,
            galery_5,
            galery_6,
            galery_7,
            galery_8,
        ],
        statistics: [
            {
                label: "Fletes y mudanzas",
                value: '+150',
            },
            {
                label: "Reparaciones y mantenimiento",
                value: '+400',
            },
            {
                label: "Instalaciones",
                value: '+100',
            },
        ],
    }
},
components:{
    LandingLayout,
    PrimaryButton,
    StatisticCard,
    Footer
},
props:{

},
methods:{
    updateCarouselHeight() {
      const width = window.innerWidth;
      if (width < 430) {
        this.galeryCarouselHeight = '300px';
      } else if (width >= 430 && width < 1024) {
        this.galeryCarouselHeight = '430px';
      }
    },
    goToWhatsApp() {
      const url = "https://api.whatsapp.com/send?phone=523313825055&text=Hola!%20vi%20tu%20página%20de%20fletes%20y%20reparaciones.%20Me%20interesa%20su%20servicio!";
      window.open(url, "_blank", "noopener,noreferrer");
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
  color: #292929;
  opacity: 0.75;
  line-height: 150px;
  margin: 0;
  text-align: center;
}

.el-carousel__item:nth-child(2n) {
  background-color: #292929;
}

.el-carousel__item:nth-child(2n + 1) {
  background-color: #292929;
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