<template>
  <div>
    <form class="subscription-form">
      <h2>Suscríbete a Nuestro Boletín</h2>
      <div class="form-group">
        <label for="name">Usuario:</label>
        <input type="text" id="name" v-model="name" placeholder="Tu nombre" />
      </div>
      <div class="form-group">
        <label for="email">Correo Electrónico:</label>
        <input
          type="email"
          id="email"
          v-model="email"
          placeholder="tucorreo@example.com"
        />
      </div>
      <button @click="subscribe">Suscribirse</button>
    </form>
  </div>
</template>

<style scoped>
.subscription-form {
  max-width: 400px;
  margin: 0 auto;
  background-color: #f4f4f4;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80%; /* Ajusta el ancho del formulario según tu preferencia */
}

/* Estilo para pantallas de teléfono */
@media (max-width: 768px) {
  .subscription-form {
    width: 90%; /* Puedes ajustar el ancho para pantallas de teléfono */
  }
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input {
  width: 90%;
  padding: 12px;
  border: 3px solid #ccc;
  border-radius: 20px;
}

button {
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
    };
  },
  methods: {
    subscribe() {
      // Aquí puedes agregar la lógica para enviar los datos a tu servidor o realizar cualquier acción necesaria.
      // Por ejemplo, puedes utilizar axios para hacer una solicitud HTTP POST a tu servidor.
      console.log('Nombre:', this.name);
      console.log('Correo Electrónico:', this.email);
      // Luego, puedes restablecer los campos del formulario si es necesario.
      this.name = '';
      this.email = '';
    },
  },
};
</script>
