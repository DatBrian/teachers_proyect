<template>
    <section>
        <h3>Añadir profesor</h3>
        <div>
            <label>Nombre:</label>
            <input type="text" v-model="teacher.name">
        </div>
        <div>
            <label>Apellidos:</label>
            <input type="text" v-model="teacher.surname">
        </div>
        <div>
            <label>DNI:</label>
            <input type="text" v-model="teacher.dni">
        </div>
        <div>
            <label>Materias:</label>
            <input type="text" v-model="subject">
            <button @click="handleSubject()">Añadir Materia</button>
        </div>
        <div>
            <ul>
                <li v-for="(subj, index) in teacher.subjects" v-bind:key="index">{{ subj }}</li>
            </ul>
        </div>
        <input type="checkbox" v-model="teacher.doc">Documentación entregada
        <button>Agregar</button>
    </section>

    <section>
        <h3>Listado de profesores</h3>
    </section>
</template>

<script lang="ts" setup>
import { Ref, ref } from 'vue';

interface ITeacher {
    name: string,
    surname: string,
    dni: number,
    subjects: Array<string>,
    doc: boolean
}

let teacher: Ref<ITeacher> = ref({
    name: '',
    surname: '',
    dni: '',
    subjects: [],
    doc: false
});

let teachers: Ref<Array<ITeacher>> = ref([

]);

let subject: Ref<string> = ref('');

const handleSubject = () => {
    teacher.value.subjects.push(subject.value);
    subject.value = '';
}

const handleAddTeacher = () => {
    teachers.value.push(teacher.value);
    
}

</script>

<style scoped></style>