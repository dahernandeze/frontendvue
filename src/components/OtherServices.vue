<template>
    <div id="our-services">
        <section class="contenedor1 services" id="services">
            <img src="../assets/terceraIlustracion.svg" alt="">
            <div class="box-skills">
                <h4><b-icon class="b-icon" icon="check-circle"></b-icon> Web development</h4>
                <h4><b-icon class="b-icon" icon="check-circle"></b-icon> SEO</h4>
                <h4><b-icon class="b-icon" icon="check-circle"></b-icon> MKT digital</h4>
                <h4><b-icon class="b-icon" icon="check-circle"></b-icon> Web design</h4>
                <h4><b-icon class="b-icon" icon="check-circle"></b-icon> Free suport</h4>
            </div>
        </section>
    </div>
</template>

<style scoped>
.services{
    display: flex;
    justify-content: space-around;
    font-family: sans-serif;
}

.services>img{
    width: 500px;
}

.box-skills{
    margin: 30px 30px 0 0;
    
    
}

.box-skills h4{
    font-size: 24px;
    background: var(--light-gray);
    width: 350px;
    border-radius: 6px;
    padding: 10px 0 10px 30px;
    margin-bottom: 10px; 
    text-align: left;
     

}

.box-skills .b-icon{
    color: var(--light-green);
    font-size: 20px;
    
    
}


</style>