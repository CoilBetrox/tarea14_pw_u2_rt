<template>
    <div>
        <input type="text" placeholder="Ingrese una IP">
        <p></p>
        <div class="cont-btn">
            <label class="btn-consulta" v-on:click="obtenerIp">Consultar</label>
        </div>
        <p></p>
        <div class="obj-conten">
            <label class="izq">Tipo de Ip: </label>
            <label class="der">{{ tipo }}</label>

            <label class="izq">Continente: </label>
            <label class="der">{{ continente }}</label>

            <label class="izq">País: </label>
            <label class="der">{{ pais }}</label>

            <label class="izq">Región: </label>
            <label class="der">{{ region }}</label>

            <label class="izq">Ciudad: </label>
            <label class="der">{{ ciudad }}</label>

            <label class="izq">Organización: </label>
            <label class="der">{{ org }}</label>

            <label class="izq">Proveedor de Internet: </label>
            <label class="der">{{ proveedor }}</label>

            <label class="izq">Imagen: </label>
        </div>
            <img v-if="img" :src="img" alt="imagen no encontrada"/>

    </div>
</template>

<script>

export default {
    data (){
        return{
            ip:"",
            tipo:null,
            continente:null,
            pais:null,
            region:null,
            ciudad:null,
            org:null,
            proveedor:null,
            img:null
        }
    },
    methods:{
        async obtieneDetalleIp(){
            const { type, continent, country, region, city, connection, flag } = 
                await fetch('https://ipwho.is/'+this.ip).then(r=>r.json());
            this.tipo = type;
            this.continente = continent;
            this.pais = country;
            this.region = region;
            this.ciudad = city;
            const {org, isp} = connection
            this.org = org;
            this.proveedor = isp;
            const {img} = flag;
            this.img = img;
        },
        obtenerIp(){
            this.obtieneDetalleIp();
        }
    }

}
</script>

<style>

label{
    display: block;
}

.obj-conten{
    display: grid;
    grid-template-columns: repeat(2, 50%);
}

.izq{
    text-align: right;
    
}

.der{
    text-align: left;
    text-indent: 20px;
}

.cont-btn{
    display: flexbox;
    align-content: center;
}

.btn-consulta{
    text-align: center;
    margin-left: 35%;
    margin-right: 35%;
    background-color: goldenrod;
    color: black;
    border-radius: 3px;
    cursor: pointer;
}

.btn-consulta:hover{
    background-color:black;
    color: goldenrod;
}

img{
    width: 35%;
    height: 35%
}

</style>