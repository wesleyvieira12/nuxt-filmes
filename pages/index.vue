<script setup>
const busca = ref('')


const apiKey = '547bb99812e5451680924dd93518a2e6'

const { data: filmes } = await useFetch(`https://api.themoviedb.org/3/movie/popular?api_key=${apiKey}&language=en-US&page=1`)

const buscaFilmes = async () => {
    if(!busca.value) return
    const { data: filmes_buscados } = await useFetch(`https://api.themoviedb.org/3/search/movie?api_key=${apiKey}&query=${busca.value}`)
    filmes.value = filmes_buscados.value
}

</script>

<template>
    <div>
        <div class="flex gap-4">
            <Input v-model="busca" placeholder="Buscar seu filme"/>
            <Button @click="buscaFilmes"><Icon name="ic:round-search"/> Buscar</Button>
        </div>
        <h2 class="text-2xl font-bold my-8"><Icon name="solar:tv-broken"/> Filmes</h2>
        <ul class="grid grid-cols-1 gap-4 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
            <li v-for="filme in filmes.results" :key="filme.id">
                <Card class="flex flex-col items-center">
                    <CardHeader>
                        <img :src="`https://image.tmdb.org/t/p/w500${filme.poster_path}`" alt="imagem do filme" class="w-[250px]"/>
                    </CardHeader>
                    <CardContent class="flex flex-col gap-4">
                        <h3 class="text-lg font-bold">{{ filme.title }}</h3>
                        <NuxtLink :to="`/filme/${filme.id}`">
                            <Button>Ver detalhes</Button>
                        </NuxtLink>
                    </CardContent>
                </Card>
            </li>
        </ul>
    </div>
</template>