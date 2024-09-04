<template>
    <div style="margin-top: 10vh;">
        <v-container>
            <h2><center>NEWS</center></h2>
            <v-row>
                <v-col cols="12" md="6">
                    <v-card v-if="latestNews.length > 0">
                        <v-title>{{latestNews[0].title}}</v-title><br>
                        <v-subtitle>{{latestNews[0].summary}}</v-subtitle>
                    </v-card>
                </v-col>
                <v-col cols="12" md="3" v-for="(news, index) in latestNews.slice(1)" :key="news.id">
                    <v-card>
                        <v-title>{{news.title}}</v-title><br>
                        <v-subtitle>{{news.summary}}</v-subtitle>
                    </v-card>
                </v-col>
                <v-col cols="12" md="3" colspan="3">
                    <v-card>
                        aaaaa
                    </v-card>
                </v-col>
            </v-row>
        </v-container>
    </div>
</template>

<script setup>
const latestNews = [
    { id: 1, title: 'Pope to Indonesian authorities: “Interreligious dialogue fosters mutual respect”', date: '2023-10-01', summary: 'Summary of latest news 1', link: '#' },
    { id: 2, title: 'On board with Pope Francis', date: '2023-10-02', summary: 'Summary of latest news 2', link: '#' },
    { id: 3, title: 'Pope to Italian youths: “Never be resigned to war!”', date: '2023-09-30' },
    { id: 4, title: 'Interreligious dialogue at the heart of Pope\'s visit to Indonesia', date: '2023-09-29' },
    { id: 5, title: 'Pope”', date: '2023-09-30' },
    { id: 6, title: 'Pope\'s visit to Indonesia', date: '2023-09-29' },
    { id: 7, title: 'visit to Indonesia', date: '2023-09-29' },
    { id: 8, title: 'to Indonesia', date: '2023-09-29' },
    { id: 9, title: 'Indonesia', date: '2023-09-29' },
    { id: 10, title: 'Pope\'s visit ', date: '2023-09-29' },
    { id: 11, title: 'Pope\'s visit to ', date: '2023-09-29' },
    { id: 12, title: 'Pope\'s visit to Indonesia hehehehe', date: '2023-09-29' },

    
    // Add more latest news items
]
</script>

<style scoped>
/* Add any custom styles here */
</style>