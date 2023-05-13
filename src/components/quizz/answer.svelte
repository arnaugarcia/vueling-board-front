<script>
   export let option;
   export let index;
</script>

<div class="col-md-6 mb-md-0 mb-4 mt-4">
    <div class="card border shadow-none">
        <div class="card-body text-center">

            <img src={"/assets/img/quiz/option" + index + ".svg"}>
            <h5 class="my-2">{option.title}</h5>

        </div>
    </div>
</div>