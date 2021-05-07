<template>
        <div id="isPlaniSaha">
        <div class="row" >
            <div class="col-8">
                <div class="row">
                <div class="col">
                    <span>{{item.il_kodu}}</span>
                </div>
                <div class="col ">
                    <span>{{item.numarataj}}</span>
                </div>
                <div class="col ">
                    <span>{{item.geometri}}</span>
                </div>
                <div class="col ">
                    <span>{{item.toplam_is}}</span>
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