<template>
    <LandingLayout :title="'Servicios'">
        <!-- sección 1 Galería de trabajos -->
            <section class="py-24 px-5 lg:mx-32">
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
    </LandingLayout>
</template>

<script>
//general
import LandingLayout from '@/Layouts/LandingLayout.vue';

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
    }
},
components:{
    LandingLayout
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