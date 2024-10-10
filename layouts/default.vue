<template>
    <div class="flex flex-col bg-green-400 min-h-screen">
        <header class="flex items-center justify-center py-5">
            <h1 class="text-3xl font-bold">NUXT FILMES</h1>
        </header>
        <div class="container flex-grow">
            <slot />
        </div>
        <footer class="flex items-center justify-center py-5">
            <p>next3@2024</p>
        </footer>
    </div>
</template>