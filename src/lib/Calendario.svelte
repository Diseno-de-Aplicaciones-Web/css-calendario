<script>

    import Dia from "./Dia.svelte";
    import Evento from "./Evento.svelte";
    export let mes
    export let ano
    export let eventos
    let diasCosEventos = {}

    function eDesteMes(data, mes) {
        return (new Date(data).getMonth()+1) === mes
    }

    function eDesteAno(data, ano) {
        return new Date(data).getFullYear() === ano
    }

    function eUnhaData(data) {
        // .valueOf entrega NaN cando a data é creada con datos inválidos
        
        return ! isNaN(new Date(data).valueOf()) && parseInt(data.split("-")[1]) === new Date(data).getMonth()+1
    }

    function eUnhaDataDesteMes(data, mes, ano) {
        return eUnhaData(data) && eDesteAno(data, ano) && eDesteMes(data, mes)
    }

    // Construe días do mes
    for (
        let dia=1, data=`${ano}-${mes}-${dia}`;
        eUnhaDataDesteMes(data, mes, ano);
        dia++, data=`${ano}-${mes}-${dia}`
    ) {
        diasCosEventos[dia] = []
    }

    // Inserta eventos no seu dia, se son deste mes e a data é valida
    eventos.forEach( evento => {
        if ( eUnhaDataDesteMes(evento.data, mes, ano) ) {
            const diaDoMes = new Date(evento.data).getDate()
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
    grid-template-rows: repeat(6, 1fr);
}

</style>