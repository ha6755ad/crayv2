<template>
    <v-card hover>
        <v-img
        :src="app.logo"
        aspect-ratio="1.5"
        ></v-img>

        <v-card-title primary-title>
        <div>
            <h3 class="headline mb-0">{{ app.name }}</h3>
            <div> {{ app.description }} </div>
        </div>
        </v-card-title>

        <v-card-actions>
        <v-btn flat color="orange">Share</v-btn>
        <v-btn flat color="orange">Explore</v-btn>
        </v-card-actions>
    </v-card>
</template>
