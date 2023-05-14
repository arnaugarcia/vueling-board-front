<style>
    @import '/css/pages/page-faq.css';
</style>
<script>
    import AnswerComponent from '/src/components/quizz/answer.svelte'
    import {onMount} from "svelte";
    import {getCookie} from "svelte-cookie";

    const cookie = getCookie('auth');

    if (!cookie || cookie === '') {
        window.location.href = '/games/login';
    }
    let answers = [
        {id: '0', title: 'Respuesta 1'},
        {id: '1', title: 'Respuesta 2'},
        {id: '2', title: 'Respuesta 3'},
        {id: '3', title: 'Respuesta 4'}
    ];
    let question = 'prueba1'
    let id = 0;
    let options = 'http://localhost:3000/questions/' + id + '/options';

    onMount(() => {
        fetch('http://localhost:3000/questions')
            .then(responses => responses.json())
            .then(data => {
                question = data.questionText;
                id = data.id;
            });

    })
    onMount(() => {
        fetch(options)
            .then(responses => responses.json())
            .then(data => {
                answers[0].title = data[0].title;
            });

    })


</script>

<div class="container-xxl flex-grow-1 container-p-y">
    <div class="faq-header d-flex flex-column justify-content-center align-items-center rounded">
        <h3 class="text-center">{question}</h3>
    </div>
</div>
<div class="row">
    <div class="col-lg- mx-auto mb-4">
        <div class="row">
            {#each answers as answer, i}

                <AnswerComponent option={answer} index={i}/>

            {/each}
        </div>
    </div>
</div>
