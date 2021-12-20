<template>
      <div class="row">
            <div class="col-sm-6 col-md-4 col-lg-4">
                <form id="new-prod" class="hide" @submit.prevent="productInsert">
                    <fieldset>
                        <legend>Nuevo producto</legend>                          
                            <div class="form-group">
                                <label for="newprod-name">id: </label>
                                <input type="text" class="form-control" id="newprod-id" disabled>
                            </div>
                            <div class="form-group">
                                <label for="newprod-name">Nombre: </label>
                                <input type="text" class="form-control" id="newprod-name" v-model="newProduct.name">
                            </div>
                            <div class="form-group">
                                <label for="newprod-price">Price: </label>
                                <input type="text" class="form-control" id="newprod-price" v-model.number="newProduct.price">
                            </div>
                            <div class="form-group">
                                <label for="newprod-price">units: </label>
                                <input type="text" class="form-control" id="newprod-units" v-model.number="newProduct.units">
                            </div>
                        <button type="submit" class="btn btn-default btn-primary">Añadir</button>
                        <button type="reset" class="btn btn-secondary">Reset</button>
                    </fieldset>
                </form>
            </div>
        </div>   
</template>

<script>
import API from '../services/API'
export default {
    name:'form',
    data(){
        return{
            newProduct:{
                name:"",
                price:"",
                units:""
            }
        }
    },
    methods:{
        productInsert(){
            if (this.newProduct.name === "") {
                alert("nombre mal")
            }else if (this.newProduct.price <= 0) {
               alert('precio mal') 
            }else if (this.newProduct.units <= 0) {
               alert('units mal') 
            }else{
                API.products.create(this.newProduct)
            }
        }
    }
}
</script>