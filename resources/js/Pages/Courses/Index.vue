<template>
    <!-- On convertit le component AppLayout (CamelCase) en kebab-case -->
    <app-layout>

        <!-- On affiche le slot header de AppLayout.vue -->
        <template #header>
            Liste des formations
        </template>

        <div class="py-3" v-for="course in this.courseList" v-bind:key="course.id">
            <div class="mx-8 bg-white rounded shadow p-4">
                <div class="text-sm text-gray-400">Published by {{ course.user.name }} - 
                    <span class="text-gray-500 text-sm">{{ course.participants }} watcher<span v-if="parseInt(course.participants) > 1">s</span></span></div>
                <div class="flex justify-between items-center">
                    <div class="text-4xl">{{ course.title }}</div>
                    <div class="text-sm text-gray-400">{{ course.episodes_count }} episodes</div>
                </div>
                
                <div class="text-sm text-gray-600">{{ course.description }}</div>
                <a :href="'courses/' + course.id" class="bg-indigo-500 text-white px-2 py-1 text-sm inline-block mt-3 rounded hover:bg-indigo-700">Voir la formation</a>
            </div>
        </div>

    </app-layout>
</template>

<script>

    import AppLayout from './../../Layouts/AppLayout';

    export default {
        components: {
            AppLayout,
        },

        props: ['courses'],
        
        data(){
            return{
                courseList: this.courses
            }
        },

        mounted(){
            console.log(this.courses);
        }
    }
</script>
