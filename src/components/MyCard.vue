<template>
    <q-card class="my-card" flat bordered>
        <div>
            <img :src="imageSrc" class="rounded-img">
        </div>
        <q-card-actions class="q-pa-sm">
            <q-avatar><img :src="avatarSrc"></q-avatar>
            <div class="col q-px-sm">
                <div class="text-h6 text-bold text-capitalize main-title">{{ title }}</div>
                <div class="text-subtitle2 text-capitalize">by {{ author }}</div>
                <div class="text-capitalize">{{ watchCount }} watching</div>
            </div>
        </q-card-actions>
    </q-card>
</template>

<script>
export default {
    props: {
        imageSrc: String,
        avatarSrc: String,
        title: String,
        author: String,
        watchCount: Number
    }
};
</script>

<style scoped>
.my-main-card {
    width: 23%;
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

.main-title {
    display: -webkit-box;
    -webkit-line-clamp: 1;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
}

@media (max-width: 600px) {
    .my-main-card {
        width: 44%;
    }
}

@media (max-width: 320px) {
    .my-main-card {
        width: 100%;
    }
}
</style>
