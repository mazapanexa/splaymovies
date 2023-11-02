<template>
  <div>
    <div class="container">
          <div class="filters" v-if="showInStreamPlay"> <!-- Muestra el menú solo en StreamPlay -->
      <div class="filters">
        <h2>Filtrar</h2>
        <button
          @click="filterByGenre(null)"
          :class="{ active: selectedGenre === null }"
        >
          Todas
        </button>
        <button
          @click="filterByGenre(1)"
          :class="{ active: selectedGenre === 1 }"
        >
          Acción
        </button>
        <button
          @click="filterByGenre(2)"
          :class="{ active: selectedGenre === 2 }"
        >
          Animación
        </button>
        <button
          @click="filterByGenre(3)"
          :class="{ active: selectedGenre === 3 }"
        >
          Ciencia Ficción
        </button>
        <button
          @click="filterByGenre(4)"
          :class="{ active: selectedGenre === 4 }"
        >
          Terror
        </button>
      </div>
      <div class="items">
        <ProductCard
          v-for="product in filteredProducts"
          :key="product.id"
          :product="product"
          class="product-card"
        />
      </div>
    </div>
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue';

export default {
  components: {
    ProductCard,
  },
  props: {
   
    showInStreamPlay: {
      type: Boolean,
      default: true, // Por defecto, el menú de filtros no se muestra en StreamPlay
    },
  },
  data() {
    return {
      //showInAll: true,
      selectedGenre: null,
      products: [
        {
          id: 1,
          name: 'Transformers 1',
          duracion: 2,
          minutos: 23,
          genero: 'Ciencia ficción',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/qe1tFtmKtyiw8OjlCgs7cSqqF8s.jpg', // Reemplaza con el enlace de la imagen de Transformers 1 en Google Drive
          link: 'https://watchfun.fun/bu/?key=UGLAVkAYXKwCSZu-tyt-GKmoupTfhYu0tv_ghh_wYCespx9J-tyt-RRs6XIc549uuYuFDZ_ghh_NFS9iqj5joR5Cv2cbBYHGWCv_ghh_IYTqo3PW8hKL0osZ3GQTCK9AjSTHxOj3mlBbKKP5ltNM', // URL de la película Transformers 1
          numgenero: 3,
          ocultar: true,
        },
        {
          id: 2,
          name: 'Transformers 2',
          duracion: 2,
          minutos: 29,
          genero: 'Ciencia ficción',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/hDdTUHlxq6AVOsLG6RVeKP6wGM8.jpg',
          link: 'https://wishembed.pro/e/jxcgt3gzkxnx', // URL de la película Transformers 2
          numgenero: 3,
          ocultar: true,
        
        },
        {
          id: 3,
          name: 'Transformers 3',
          duracion: 2,
          minutos: 34,
          genero: 'Ciencia ficción',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/fMqXNNgzTaxalU1ve9KevpELiGe.jpg',
          link: 'https://waaw.to/f/3gLEjwtT8c7R',
          numgenero: 3,
          ocultar: true,
          
        },
        {
          id: 4,
          name: 'Transformers 4',
          duracion: 2,
          minutos: 45,
          genero: 'Ciencia ficción',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/gNHcZ41J6vNEkICd95FETGwiWho.jpg',
          link: 'https://azipcdn.com/v/q4w3ejy4rcwm',
          numgenero: 3,
          ocultar: true,
          
        },
        {
          id: 5,
          name: 'Transformers 5',
          duracion: 2,
          minutos: 29,
          genero: 'Ciencia ficción',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/yTSaTtpWsZzYGdIp1RjxWX1lC7C.jpg',
          link: 'https://azipcdn.com/v/q4w3ejy4rcwm',
          numgenero: 3,
          ocultar: true, 
        
        },
        {
          id: 6,
          name: 'Blade Runner 2049',
          duracion: 2,
          minutos: 44,
          genero: 'Ciencia ficción',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/aBvDBfqCHs0sCXoun7giyHeClb1.jpg',
          link: 'https://azipcdn.com/v/armzk7yyzgyl',
          numgenero: 3,
          ocultar: true,
        
        },
        {
          id: 7,
          name: 'Rápidos y Furiosos X',
          duracion: 2,
          minutos: 44,
          genero: 'Acción',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/l31hvzHjfj903hGBgL1v3uGGwU8.jpg',
          numgenero: 1,
          ocultar: true,
          
        },
        {
          id: 8,
          name: 'Spider-Man',
          duracion: 2,
          minutos: 1,
          genero: 'Ciencia ficción',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/2ufIbl01RhJ9QkSUxD0UjDakxvk.jpg',
          link: 'https://www.google.com/',
          numgenero: 3,
          ocultar: true,
        
        },
        {
          id: 9,
          name: 'El increíble hulk',
          duracion: 1,
          minutos: 53,
          genero: 'Ciencia ficción',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/p4NYZXVtgKf6aiH65QzzkUVJcsd.jpg',
          link: 'https://www.google.com/',
          numgenero: 3,
          ocultar: true,
        
        },
        {
          id: 10,
          name: ' Scooby-Doo y Krypto',
          duracion: 1,
          minutos: 19,
          genero: 'Animacion',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/oWspFZp0lfYeykiaPIabaGtiA6U.jpg',
          link: 'https://www.google.com/',
          numgenero: 2,
          ocultar: true,
          
        },
        {
          id: 11,
          name: 'Midsommar: El terror no espera la noche',
          duracion: 2,
          minutos: 28,
          genero: 'Terror',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/km0ta4N96yjoZPVy5A3gbcE3Ne8.jpg',
          link: 'https://www.google.com/',
          numgenero: 4,
          ocultar: true,
          
        },
        {
          id: 12,
          name: 'Spider-Man: A través del Spider-Verso',
          duracion: 2,
          minutos: 20,
          genero: 'Animacion',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/37WcNMgNOMxdhT87MFl7tq7FM1.jpg',
          link: 'https://www.google.com/',
          numgenero: 2,
          ocultar: true,
        },
         {
          id: 13,
          name: 'Annabel: El Conjuro',
          duracion: 1,
          minutos: 39,
          genero: 'Terror',
          imageUrl:
            'https://www.themoviedb.org/t/p/original/y84GATalgc1VA0GzyFNxCmAHkTN.jpg',
          link: 'https://www.google.com/',
          numgenero: 4,
         
          
        },
        {
        id:14,
        name: 'Teror bajo la Tierra 5: Lineas de sangre',
        duracion: 1,
        minutos: 39,
        genero: 'Terror',
        imageUrl: 'https://www.themoviedb.org/t/p/original/eJ2kxo6yzwYvqUOGOBjXTaO8oYQ.jpg',
        link: 'https://www.google.com/',
        numgenero: 4,
        },      
        {
        id:15,
        name: 'Ballerina',
        duracion: 1,
        minutos: 33,
        genero: 'Terror',
        imageUrl: 'https://www.themoviedb.org/t/p/original/bcwSsl9pw8ogjNsdwKbcVjMW8eZ.jpg',
        numgenero: 4,
        },
        {
        id: 16,
        name: 'M3GAN',
        duracion: 1,
        minutos: 42,
        genero: 'Terror',
        imageUrl: 'https://www.themoviedb.org/t/p/original/ogSpQMynabVu91Bi7AuUA8tshfb.jpg',
        numgenero: 4,
        },
        {
        id: 17,
        name: 'Scream 6',
        duracion: 2,
        minutos: 3,
        genero: 'Terror',
        imageUrl: 'https://www.themoviedb.org/t/p/original/rOXdbT6U8q6aEBZ0AvVpXpwAXuK.jpg',
        numgenero: 4,
        },
        {
      	id: 18,
	      name: 'Megalodón',
	      duracion: 1,
	      minutos: 53,
	      genero: 'Terror',
      	imageUrl: 'https://www.themoviedb.org/t/p/original/pQARFwPxjZ04ylcE5PmWfqQI1Jw.jpg',
	      numgenero: 4,
	      },
        {
	      id: 19,
	      name: 'El exorcista del Papa',
      	duracion: 1,
      	minutos: 49,
      	genero: 'Terror',
      	imageUrl: 'https://www.themoviedb.org/t/p/original/qcknZEeD71byJ3XSalDDZ5iHpNr.jpg',
      	numgenero: 4,
	      },
                {
	      id: 20,
	      name: 'Five Nights at Freddy’s',
      	duracion: 1,
      	minutos: 43,
      	genero: 'Terror',
      	imageUrl: 'https://www.themoviedb.org/t/p/original/gk5t2xWmtcUjvhoUmvdymY3nR8r.jpg',
      	numgenero: 4,
	      },
        // Agrega más productos aquí

        // ...
      ],
    };
  },
  computed: {
    filteredProducts() {
      return this.products.filter((product) => {
        if (this.selectedGenre === null) {
          return product.showInAll || product.ocultar;
        } else {
          return product.numgenero === this.selectedGenre;
        }
      });
    },
  },
  methods: {
    filterByGenre(genre) {
      this.selectedGenre = genre;
    },
  },
};
</script>

<style scoped>
/* Estilos del filtro */
.filters {
  background-color: #007bff;
  padding: 10px;
  text-align: center;
  min-height: 100px; /* Establece una altura mínima para evitar el desplazamiento */
}

.filters h2 {
  font-size: 1.2rem;
  margin: 0;
  color: #000;
}

/* Cambia los botones de 'block' a 'inline-block' y ajusta el margen para separarlos */
.filters button {
  display: inline-block;
  margin: 5px 10px;
  padding: 5px 10px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.filters button.active {
  background-color: #0056b3;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
/* Estilos del filtro */

/*se modificara a apartir de aqui*/
/*
.items {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}*/

/*codigo de pantallas */
.items {
  display: grid;
  gap: 20px;
}

/* Media Query para pantallas más grandes, como PC o tabletas */
@media (min-width: 768px) {
  .items {
    grid-template-columns: repeat(4, 1fr);
    justify-items: center; /* Centra las tarjetas horizontalmente */
  }
}

/* Media Query para pantallas más pequeñas, como teléfonos */
@media (max-width: 767px) {
  .items {
    grid-template-columns: 1fr;
    justify-items: center; /* Centra las tarjetas horizontalmente */
  }
}


/*codigo de pantallas */
.product-card {
  border: 1px solid #ccc;
  padding: 10px;
  text-align: center;
  background-color: #f8f8f8;
  box-shadow: 0 0 5px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
}

.product-image img {
  width: 100%;
  height: auto;
  border-radius: 5px 5px 0 0;
}

.product-card h2 {
  font-size: 0.9rem;
  margin: 10px 0;
}

.duration {
  font-size: 1rem;
  margin: 5px 0;
}

.watch-button {
  display: inline-block;
  padding: 5px 10px;
  background-color: #007bff;
  color: #fff;
  text-decoration: none;
  border-radius: 5px;
  font-weight: bold;
  transition: background-color 0.3s;
}

.watch-button:hover {
  background-color: #0056b3;
}
</style>
