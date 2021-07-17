<template>
    <from @submit.prevent='saveProduct'>
        <div class='col-lg-5 col-md-5 col-sm-12 col-xs-12'>
            <div class='from-group'>
               <label> Name </label>
               <input
                  type="text"
                  placeholder="Name"
                  v-model="model.name"
                  name="name"
                  class='form-control'
               />
            </div>
            <div class="form-group">
                <label> Price </label>
                <input 
                   type="number"
                   class="form-control"
                   placeholder="Price"
                   v-model="model.Price"
                   name = "price"
                />
            </div>
            <div class="from-group">
               <label> manufacturer </label>
               <select
                class="foem-control"
                type="text"
                v-model="model.manufacturer"
                name="manufacturer">
                <div v-for="manufacturer in manufacturers" :key="manufacturer._id">
                    <option :value="manufacturer._id" :selected="manufacturer._id == (model.manufacturer && model.manufacturer._id)">{{manufacturer.name}}</option>
                </div>
               </select>
            </div>
        </div>

        <div class="col-lg-4 col-md-4 col-sm-12 col-xs-12">
            <div class="form-group">
                <label>Image</label>
                <input
                type="text"
                placeholder="Image"
                v-model="model.image"
                name="image"
                class="form-control" />
            </div>
            <div class="form-group">
                <label>Description</label>
                <textarea
                class="form-control"
                placeholder="Description"
                rows="5"
                v-model="model.description"
                name="description"
                ></textarea>
            </div>
            <div class="form-group new-button">
                <button class="button">
                <i class="fa fa-pencil"></i>
                <!-- Conditional rendering for input text -->
                <span v-if="isEditing">Update Product</span>
                <span v-else>Add Product</span>
                </button>
            </div>
        </div>
    </from>
</template>


<script>

export default  {
    props: ['model','manufacturers','isEditing'],

    methods:{
        saveProduct(){
            this.$emit('save-prodect', this.model);
        }
    }
}
</script>

