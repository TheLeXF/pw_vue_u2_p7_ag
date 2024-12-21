<template>
    <img :src=img :alt=txtAlt>

    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta">

    <p>Recuerda cuando finalices tu pregunta da un ?</p>
    <h1>{{pregunta}}</h1>
    <h2>{{respuesta}}</h2>
</template>

<script>
export default {
    data(){
        return{
            pregunta:'Hola mundo',
            img:"https://yesno.wtf/assets/yes/5-64c2804cc48057b94fd0b3eaf323d92c.gif",
            txtAlt:"Nose puede ver",
            respuesta:null
        }
    }, 
    methods:{
        async llamarAPI(){
            const data = await fetch('https://yesno.wtf/api').then(resp=>resp.json());
            this.respuesta=data.answer;
            this.img=data.image;
            console.log(data);
        },
        async fachada(){
            await this.llamarAPI();
        }
    },
    watch:{
        pregunta(value, oldValue){
            console.log(value);
            console.log(oldValue);
            if(value.includes('?')){
                //Programar la llamada al API para obtener el si y el no y la imagen
                console.log('Aqui llamo al API')
                this.fachada();
            }
        }
    }
    
};
</script>

<style>

</style>