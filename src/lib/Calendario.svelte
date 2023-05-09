<script>

    import Dia from "./Dia.svelte";
    import Evento from "./Evento.svelte";
    export let mes
    export let ano
    export let eventos
    let diasCosEventos = {}

    function eDesteMes(data) {
        return (new Date(data).getMonth()+1) === mes
    }

    function eDesteAno(data) {
        return new Date(data).getFullYear() === ano
    }

    // Construe días do mes
    for (
        let dia=1, data=new Date(`${ano}/${mes}/${dia}`);
        ! isNaN(data);
        dia++, data=new Date(`${ano}/${mes}/${dia}`)
    ) {
        diasCosEventos[dia] = []
    }

    // Inserta eventos no seu dia, se son deste mes
    eventos.forEach( evento => {
        const dataDoEvento = new Date(evento.data)
        const diaDoMes = dataDoEvento.getDate()
        if ( eDesteAno(dataDoEvento) && eDesteMes(dataDoEvento) ) {
            diasCosEventos[diaDoMes].push(evento)
        }
    })

</script>

<div class="calendario">

    {#each Object.entries(diasCosEventos) as [dia, eventos]}
    <Dia data={`${ano}-${mes}-${dia}`}>
        {#each eventos as evento}
        <Evento evento={evento}/>
        {/each}
    </Dia>
    {/each}

</div>


<style>

.calendario {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    grid-template-rows: repeat(7, 1fr);
}

</style>