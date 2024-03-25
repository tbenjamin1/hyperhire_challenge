<template>
  <div class="q-gutter-md">
    
    <div class="q-pa-sm row justify-center ">
      <!-- Duplicate the first image link 5 times -->
      <div class=" my-main-card q-col-md-3" v-for="index in 5" :key="'mountains-' + index">
        <q-card class="my-card" flat bordered>
          <div>
            <img src="https://cdn.quasar.dev/img/mountains.jpg" class="rounded-img">
          </div>

         <q-card-actions class=" q-pa-sm">
            <q-avatar> <img src="https://cdn.quasar.dev/img/avatar.png"></q-avatar>
            <div class="col q-px-sm " >
                 <div class="text-h6 text-bold text-capitalize main-title">Our Changing Planet </div>
                 <div class="text-subtitle2 text-capitalize">by John Doe</div>
                 <div class="text-capitalize" >5.4K watching</div>
              </div>
          </q-card-actions>
        </q-card>
      </div>

      <!-- Duplicate the second image link 2 times -->
      <div class=" my-main-card q-col-md-3" v-for="index in 2" :key="'parallax1-' + index">
        <q-card class="my-card" flat bordered>
          <img src="https://cdn.quasar.dev/img/parallax1.jpg" class="rounded-img">

         <q-card-actions class=" q-pa-sm">
            <q-avatar> <img src="https://cdn.quasar.dev/img/avatar.png"></q-avatar>
            <div class="col q-px-sm " >
                 <div class="text-h6 text-bold text-capitalize main-title ">Our Changing Planet</div>
                 <div class="text-subtitle2 text-capitalize">by John Doe</div>
                 <div class="text-capitalize" >5.4K watching</div>
              </div>
          </q-card-actions>
        </q-card>
      </div>

      <!-- Use the third image link once -->
      <div class="my-main-card q-col-md-3">
        <q-card class="my-card" flat bordered>
          <img src="https://cdn.quasar.dev/img/parallax2.jpg">

          <q-card-actions class=" q-pa-sm">
            <q-avatar> <img src="https://cdn.quasar.dev/img/avatar.png"></q-avatar>
            <div class="col q-px-sm " >
               <div class="text-h6 text-bold text-capitalize main-title">Our Changing Planet Our Changing Planet Our Changing Planet Our Changing Planet</div>
               <div class="text-subtitle2 text-capitalize">by John Doe</div>
               <div class="text-capitalize" >5.4K watching</div>
            </div>
          </q-card-actions>
        </q-card>
      </div>
    </div>
  </div>
</template>

<style scoped>
.my-main-card {
  width: 25%;
}
.my-card img {
  border-radius: 5%;
}

.q-card {
  border-radius: none;
  margin: 10px;
}

.q-card--bordered {
  border: none;
}

.rounded-img {
  object-fit: cover;
  width: 100%;
  height: 100%;
  border-radius: 10px;

}

.q-card__actions {
  padding: 8px 0px;
  align-items: flex-start;
}
.main-title{
  display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
}
@media (max-width: 600px) {
  .my-main-card {
    width: 50%;
  }
}
@media (max-width: 320px) {
  .my-main-card {
    width: 100%;
  }
}

</style>
