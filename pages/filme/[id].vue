<script setup>
const { id } = useRoute().params

const apiKey = '547bb99812e5451680924dd93518a2e6'
const { data: filme } = await useFetch(`https://api.themoviedb.org/3/movie/${id}?api_key=${apiKey}`)

</script>

<template>
    <div>
        <Card v-if="filme">
            <CardHeader class="flex flex-col items-center">
                <h2 class="text-3xl font-bold">{{ filme.title }}</h2>
                <img :src="`https://image.tmdb.org/t/p/w500${filme.poster_path}`" alt="imagem do filme" class="w-[250px]"/>
            </CardHeader>
            <CardContent>
                <p>{{  filme.overview }}</p>
                <p>{{  filme.release_date }}</p>
                <p>{{  filme.vote_average }}</p>
            </CardContent>
        </Card>
        <NuxtLink :to="'/'">
            <Button variant="link">
                <Icon name="lets-icons:back"/>Voltar
            </Button>
        </NuxtLink>
    </div>
</template>