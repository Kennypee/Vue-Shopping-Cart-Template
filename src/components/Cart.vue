<template>
    <div>
        <ul class="list-group">
        <li :key="item.id" class="list-group-item" v-for="item in items">
            {{item.title}} - ${{item.price}}
            <button @click="$emit('remove-item', item)" class="btn badge btn-danger float-right">Remove from cart</button>
        </li>
        
    </ul>
    <div class="card p-3 my-5">
        <h5 class="text-center display-7 text-muted">
            Total: ${{ total }}
        </h5>
    </div>
    <button :disabled="items.length === 0 " @click="$emit('pay')" class="btn btn-info form-control"> Pay Now</button>
    </div>
</template>
<script>
export default {
    props:['items'],
    computed:{
        total(){
            return this.items.reduce((acc, item) => acc + Number(item.price), 0)

        }
    }
    
}
</script>
