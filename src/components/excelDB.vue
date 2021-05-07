<template>
    <div class="row">
        <div class="col-md-6 offset-md-3 border d-flex justify-content-between  pt-2">
        <span class="border border-secondary">{{item.adi}}</span>
        <button class="btn">Ekle</button>
        </div>
    </div>

</template>

<script>
export default {
    props : ["item"]
    
}
</script>