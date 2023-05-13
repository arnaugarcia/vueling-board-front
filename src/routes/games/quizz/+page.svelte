<style>
    @import '/css/pages/page-faq.css';
</style>
<script>

    import AnswerComponent from '/src/components/quizz/answer.svelte'

    let answers = [
        {id : '0', title : 'Respuesta 1'},
        {id : '1', title : 'Respuesta 2'},
        {id : '2', title : 'Respuesta 3'},
        {id : '3', title : 'Respuesta 4'}];

</script>

<div class="container-xxl flex-grow-1 container-p-y">
    <div class="faq-header d-flex flex-column justify-content-center align-items-center rounded">
        <h3 class="text-center">Pregunta :)</h3>
    </div>
</div>
<div class="row">
    <div class="col-lg- mx-auto mb-4">
        <div class="row">

            {#each answers as answer}
                <AnswerComponent option={answer}/>
            {/each}
        </div>
    </div>
</div>
