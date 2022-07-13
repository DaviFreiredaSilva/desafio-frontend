<template>
  <div class="div-form m-3">
    <form @submit="formHandler" class="m-2">
     <div class="card p-4 shadow">   
      <h3>Escolha o tipo de adesivo...</h3>
      <div class="form-check d-flex">
        <input
          class="form-check-input me-2"
          type="checkbox"
          v-model="types"
          value="react"
          id="react"
        />
        <label for="react" class="form-check-label">React</label>
      </div>
      <div class="form-check d-flex">
        <input
          class="form-check-input me-2"
          type="checkbox"
          v-model="types"
          value="vue"
          id="vue"
        />
        <label for="vue" class="form-check-label">Vue</label>
      </div>
      <div class="form-check d-flex">
        <input
          class="form-check-input me-2"
          type="checkbox"
          v-model="types"
          value="angular"
          id="angular"
        />
        <label for="angular" class="form-check-label">Angular</label>
      </div>
      </div>
      <div class="card my-4 p-4 shadow">
        <h3 class="card-title">Escolha a quantidade abaixo</h3>
        <div>
          <button id="btnSub" class="btn btn-warning" @click="quantityHandler">-</button>
          <input type="number" v-model="quantity" id="quantity-input" class="m-3" min="0" step="1"/>
          <button id="btnPlus" class="btn btn-success" @click="quantityHandler">+</button>
        </div>
      </div>
      <p>Observações...</p>
      <textarea rows= "5" v-model="message" class="form-control mb-2" placeholder="Mande um recado..."></textarea>
      <button type="submit" class="btn btn-outline-primary" >Enviar</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "ShopForm",
  data: function () {
    return {
      types: [],
      quantity: 0,
      message: ""
    };
  },
  methods: {
    formHandler: function (e) {
      e.preventDefault();

      var shoppingData = "Tipos: "
      this.types.forEach((type)=> {
        shoppingData += `${type} `
      });
      
      shoppingData += `\nQuantidade: ${this.quantity} \nMensagem: ${this.message}`
      if(this.types.length !== 0 && this.quantity > 0 && this.message !== "" ){
        alert("Dados do pedido: \n"+shoppingData); 
      }else{
        alert("Por favor, preencha todos os dados.");
      }
    },
    quantityHandler: function (e) {
        e.preventDefault();
      if(this.quantity >= 0 && e.target.id === "btnPlus"){
        this.quantity ++;
      }else{
        if(this.quantity > 0 && e.target.id === "btnSub"){
            this.quantity --;
        }else {
            if(this.quantity === 0 && e.target.id === "btnSub"){
                alert("Não aceita números negativos.")
            }
        }
      }
    },
  },
};
</script>

<style scoped>
label {
  font-size: 1.3rem;
}

.card{
    border-radius: 15px;
}

.div-form {
  width: 30vw;
}

#quantity-input{
    width: 60px;
}
</style>
