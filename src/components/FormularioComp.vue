<template>
  <div class="formulario-producto">
    <h2>Registro de Producto</h2>
    <form @submit.prevent="registrarProducto" class="form-container">
      <div class="campo">
        <label for="nombre">Nombre del Producto:</label>
        <input
          type="text"
          id="nombre"
          v-model="producto.nombre"
          required
          placeholder="Ingrese el nombre del producto"
          class="input-field"
        />
      </div>

      <div class="campo">
        <label for="precio">Precio:</label>
        <input type="number" id="precio"
          v-model.number="producto.precio"
          min="0"
          step="0.01"
          required
          placeholder="0.00"
          class="input-field"
        />
      </div>

      <div class="campo">
        <label for="cantidad">Cantidad:</label>
        <input
          type="number"
          id="cantidad"
          v-model.number="producto.cantidad"
          min="1"
          required
          placeholder="Ingrese la cantidad"
          class="input-field"
        />
      </div>

      <div class="botones">
        <button type="submit" class="btn-registrar">Registrar Producto</button>
        <button type="button" @click="limpiarFormulario" class="btn-limpiar">Limpiar</button>
      </div>
    </form>

    
    <div v-if="mostrarDatos" class="producto-registrado">
      <h3>Producto Registrado:</h3>
      <p><strong>Nombre:</strong> {{ producto.nombre }}</p>
      <p><strong>Precio:</strong> ${{ producto.precio.toFixed(2) }}</p>
      <p><strong>Cantidad:</strong> {{ producto.cantidad }}</p>
      <p><strong>Total:</strong> ${{ (producto.precio * producto.cantidad).toFixed(2) }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormularioComp',
  data() {
    return {
      producto: {
        nombre: '',
        precio: 0,
        cantidad: 1
      },
      mostrarDatos: false
    }
  },
  methods: {
    registrarProducto() {
      // Validar que todos los campos estén llenos
      if (this.producto.nombre && this.producto.precio > 0 && this.producto.cantidad > 0) {
        this.mostrarDatos = true;
        console.log('Producto registrado:', this.producto);
        
        // Aquí podrías enviar los datos a una API o realizar otra acción
        alert('Producto registrado exitosamente!');
      } else {
        alert('Por favor, complete todos los campos correctamente.');
      }
    },
    limpiarFormulario() {
      this.producto = {
        nombre: '',
        precio: 0,
        cantidad: 1
      };
      this.mostrarDatos = false;
    }
  }
}
</script>

<style scoped>
.formulario-producto {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h2 {
  text-align: center;
  color: #333;
  margin-bottom: 30px;
}

.form-container {
  background: #f9f9f9;
  padding: 30px;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.campo {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
  color: #555;
}

.input-field {
  width: 100%;
  padding: 12px;
  border: 2px solid #ddd;
  border-radius: 4px;
  font-size: 16px;
  transition: border-color 0.3s;
  box-sizing: border-box;
}

.input-field:focus {
  outline: none;
  border-color: #007bff;
  box-shadow: 0 0 5px rgba(0, 123, 255, 0.3);
}

.botones {
  display: flex;
  gap: 10px;
  margin-top: 30px;
}

.btn-registrar, .btn-limpiar {
  flex: 1;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.btn-registrar {
  background-color: #28a745;
  color: white;
}

.btn-registrar:hover {
  background-color: #218838;
}

.btn-limpiar {
  background-color: #6c757d;
  color: white;
}

.btn-limpiar:hover {
  background-color: #5a6268;
}

.producto-registrado {
  margin-top: 30px;
  padding: 20px;
  background: #e8f5e8;
  border-radius: 4px;
  border-left: 4px solid #28a745;
}

.producto-registrado h3 {
  margin-top: 0;
  color: #155724;
}

.producto-registrado p {
  margin: 8px 0;
  color: #155724;
}
</style>