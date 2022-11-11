<template>
  <div>
    <b-carousel id="carousel-fade" style="text-shadow: 0px 0px 2px #000" fade controls indicators>
      <b-carousel-slide class="carousel-principal" v-for="(carousel, c) in carousels" v-bind:key="c" :caption="carousel.caption"
        :text="carousel.text" :img-src="carousel.img"></b-carousel-slide>
    </b-carousel>

    <b-container>
      <b-row class="mt-3">
        <b-col lg="4" md="6" sm="6" class="px-2 mb-4" v-for="(maqueta, m) in maquetas" v-bind:key="m">
          <div class="card-maquetas">
            <b-img :src="maqueta.principalImg" fluid />
            <div class="card-maquetas-body">
              <p>{{ maqueta.title }}</p>
              <div class="cat">{{ maqueta.categoria }}</div>
              <b-button variant="outline-danger" block v-b-modal="maqueta.md">Ver detalles</b-button>
            </div>
          </div>

          <b-modal :id="maqueta.md" :title="maqueta.title" size="xl" centered hide-footer>
            <b-row>
              <b-col lg="7" sm="12">
                <b-carousel id="carousel-fade" style="text-shadow: 0px 0px 2px #000" fade controls indicators>
                  <b-carousel-slide v-for="(maquetaImg, m) in maqueta.imgs" v-bind:key="m" :img-src="maquetaImg.img"
                    class="modal-detail-img" />
                </b-carousel>
              </b-col>
              <b-col lg="5" sm="12">
                <div class="detalles">
                  <div class="detalles-title">DETALLES</div>
                  <ul>
                    <li v-if="maqueta.categoria == 'MODELO 3D'">Costo de acuerdo a los detalles del modelo</li>
                    <li v-else>Costo de envio de acuerdo al destino</li>
                    <li v-for="(detalle, d) in maqueta.detalles" v-bind:key="d">{{ detalle }}</li>
                  </ul>
                  <b-link id="link" :href="`https://api.whatsapp.com/send?phone=${phone}Hola👋, me interesa la ${maqueta.title}`" target="_blank">
                    <b-button variant="success" block>Soliciar por Whatsapp
                      <font-awesome-icon icon="fa-brands fa-whatsapp" />
                    </b-button>
                  </b-link>
                  <b-alert show variant="info" class="mt-2">Todas las compras son exclusivamente realizadas mediante el
                    aplicativo Whatsapp</b-alert>
                  <b-alert show variant="warning">La entrega se realiza despues de haber realizado el pago
                    correspondiente</b-alert>
                </div>
              </b-col>
            </b-row>
          </b-modal>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      phone: process.env.VUE_APP_NUMERO_PHONE,
      carousels: [
        {
          img: require("@/assets/img/1-AR.jpg"),
          caption: "Maquetas Arquitectonicas",
          text: "Primer y segundo ciclo",
        },
        {
          img: require("@/assets/img/site-solar/1.jpg"),
          caption: "Maquetas del sistema solar",
          text: "Diversos tamaños y personalizacion",
        },
      ],

      maquetas: [
        {
          principalImg: require("@/assets/img/casa-jardin/1.jpg"),
          title: "Maqueta de una casa con jardín",
          categoria: "ARQUITECTURA",
          md: "md-1",
          imgs: [
            {
              img: require("@/assets/img/casa-jardin/1.jpg"),
            },
            {
              img: require("@/assets/img/casa-jardin/2.jpg"),
            },
            {
              img: require("@/assets/img/casa-jardin/3.jpg"),
            },
          ],
          detalles: [
            "Variedad de tamaños", "Decoracion a peticion del cliente", "Opcional luz ambiental"
          ]
        },
        {
          principalImg: require("@/assets/img/casa-madera/1.webp"),
          title: "Casa de madera",
          categoria: "ARQUITECTURA",
          md: "md-2",
          imgs: [
            {
              img: require("@/assets/img/casa-madera/1.webp"),
            },
            {
              img: require("@/assets/img/casa-madera/2.webp"),
            },
            {
              img: require("@/assets/img/casa-madera/3.webp"),
            },
          ],
          detalles: [
            "Variedad de tamaños", "Madera de buena calidad", "Decoracion a peticion del cliente", "Color a eleccion del cliente"
          ]
        },
        {
          principalImg: require("@/assets/img/taller/1.jpeg"),
          title: "Taller 2 UTP - Modelo 3d",
          categoria: "MODELO 3D",
          md: "md-3",
          imgs: [
            {
              img: require("@/assets/img/taller/1.jpeg"),
            },
          ],
          detalles: [
            "Entrega de la carpeta con el modelo 3d"
          ]
        },
        {
          principalImg: require("@/assets/img/casa/1.jpeg"),
          title: "Fabrica - Modelo 3d",
          categoria: "MODELO 3D",
          md: "md-4",
          imgs: [
            {
              img: require("@/assets/img/casa/1.jpeg"),
            },
            {
              img: require("@/assets/img/casa/2.jpeg"),
            },
          ],
          detalles: [
            "Maqueta + modelo 3d"
          ]
        },
        {
          principalImg: require("@/assets/img/site-solar/1.jpg"),
          title: "Maqueta del sistema solar",
          categoria: "GALAXIA",
          md: "md-5",
          imgs: [
            {
              img: require("@/assets/img/site-solar/1.jpg"),
            },
            {
              img: require("@/assets/img/site-solar/2.jpg"),
            },
            {
              img: require("@/assets/img/site-solar/3.jpg"),
            },
          ],
          detalles: [
            "Diversos tamaños", "Decoracion a peticion del cliente", "Tipo de fuente a eleccion del cliente"
          ]
        },
        {
          principalImg: require("@/assets/img/site-circulatorio/1.jpg"),
          title: "Sistema Circulatorio",
          categoria: "PRIMARIA",
          md: "md-6",
          imgs: [
            {
              img: require("@/assets/img/site-circulatorio/1.jpg"),
            },
            {
              img: require("@/assets/img/site-circulatorio/2.jpg"),
            },
            {
              img: require("@/assets/img/site-circulatorio/3.jpg"),
            },
          ],
          detalles: [
            "Diversos tamaños", "Tipo de fuente a eleccion del cliente"
          ]
        },
      ],
    };
  },

};
</script>

<style lang="scss">
@mixin mobile {
  @media only screen and (max-width: 600px) {
    @content;
  }
}

@mixin tablet {
  @media only screen and (max-width: 1280px) {
    @content;
  }
}

.carousel-principal img {
  height: 55em !important;
  width: 100% !important;
  object-fit: cover;

  @include tablet(){
    height: 35em !important;
  }

  @include mobile(){
    height: 20em !important;
  }
}

.modal-detail-img img {
  height: auto !important;
  max-height: 40em;

  @include tablet(){
    max-height: 20em !important;
    object-fit: cover;
  }
}

.card-maquetas {
  width: 100%;
  border-radius: 8px;
  box-shadow: -1px 6px 5px 0px rgba(191, 185, 185, 0.75);
  -webkit-box-shadow: -1px 6px 5px 0px rgba(191, 185, 185, 0.75);
  -moz-box-shadow: -1px 6px 5px 0px rgba(191, 185, 185, 0.75);

  img {
    width: 100%;
    object-fit: cover;
    max-height: 11rem;
  }

  &-body {
    padding: 1rem;

    .cat {
      position: absolute;
      top: 5px;
      padding: 2px 20px;
      background: rgb(240, 118, 36);
      color: #fff;
      font-weight: 600;
      border-radius: 12px;
    }
  }
}
</style>
