<template>
<div class="card my-5">
    <div class="card-body">
        <h5 class="text-center card-title">
            {{product.title}}
        </h5>
        <p class="text-center card-text text-muted display-4">
            $ {{Number(product.price).toFixed( )}}
        </p>
        <button :disabled="isAddedToCart" @click="$emit('add-to-cart'), product" class="btn btn-primary form-control ">
            {{ isAddedToCart ? 'Added To Cart': 'Add To Cart'}}
        </button>
    </div>
</div>
</template>

<script>
export default {
    props:['product', 'isAddedToCart']
}
</script>
