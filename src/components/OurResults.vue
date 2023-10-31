<template>
    <div id="results">
        <section class="results">
            <div class="contenedor1 conten-results">
                <section class="numbers">
                    <div class="number" data-aos="zoom-in-left">
                        <h4>+8863</h4>
                        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Accusamus, explicabo.</p>
                    </div>
                    <div class="number" data-aos="zoom-in-left">
                        <h4>+8863</h4>
                        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Accusamus, explicabo.</p>
                    </div>
                    <div class="number" data-aos="zoom-in-left">
                        <h4>+8863</h4>
                        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Accusamus, explicabo.</p>
                    </div>
                    <div class="number" data-aos="zoom-in-left">
                        <h4>+8863</h4>
                        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Accusamus, explicabo.</p>
                    </div>
                </section>

                <section class="results-text">
                    <h4>Lorem ipsum dolor sit amet.</h4>
                    <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Officiis, natus.</p>
                    <a href="#">Ingrese aquí</a>
                </section>
            </div>
        </section>
    </div>
</template>


<style scoped>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

#results{
    font-family: 'Roboto', sans-serif;
}

h1, h2, h3, h4, h5, h6 {
    color: var(--dark-blue);
    font-weight: 300;
    
}


.results{
    background: var(--middle-blue);
    padding-top: 30px;

}

.conten-results{
    display: flex;
    justify-content: space-evenly;

}

.numbers{
    width: 60%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;

}

.numbers .number{
    width: 45%;
    background: rgba(255, 255, 255, .2);
    color: var(--white);
    border-radius: 10px;
    padding: 40px 35px;
    margin-bottom: 20px;
    
}

.numbers .number h4{
    color: var(--white);
    font-size: 50px;
    font-weight: 500;
    margin-bottom: 20px;
}

.numbers .number p{
    color: var(--white-gray);
    font-weight: 300;
}

.results-text{
    width: 37%;
}

.results-text h4{
    color: var(--white);
    font-size: 40px;
}

.results-text p{
    color: var(--white);
    font-weight: 300;
    margin: 20px 0;

}

.results-text>a{
    color: var(--white);
    text-decoration: none;
    display: inline-block;
    border: 1px solid var(--white);
    padding: 10px 0;
    width: 120px;
    text-align: center;
    border-radius: 5px;
}

</style>