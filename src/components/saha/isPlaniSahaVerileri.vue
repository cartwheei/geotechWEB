<template>
        <div id="isPlaniSaha">
        <div class="row" >
            <div class="col-8">
                <div class="row">
                <div class="col">
                    <span>{{item.adi}}</span>
                </div>
                <div class="col ">
                    <span>{{item.adi}}</span>
                </div>
                <div class="col ">
                    <span>{{item.adi}}</span>
                </div>
                </div>
            </div>
            <div class=" col align-self-end">
              <button class="btn btn-danger">Sil</button>
              <button class="btn btn-primary">Güncelle</button>
            </div>
        </div>

    </div>
</template>

<script>
export default {
        props : ["item"]
}
</script>