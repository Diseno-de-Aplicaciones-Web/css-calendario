<script>
    export let data
    $: dataDoEvento = new Date(data)
    $: clases = `${dataADiaDaSemana(dataDoEvento)} ${dataASemanaDoMes(dataDoEvento)}`
    $: diaDoMes = dataDoEvento.getDate()

    function deInicioDomingoAInicioLunes(numeroDiaSemana) {
        return (numeroDiaSemana+6)%7
    }

    function dataADiaDaSemana(data) {
        const nomesClases = ["luns","martes","mercores","xoves","venres","sabado","domingo"]
        const numeroDoDia = deInicioDomingoAInicioLunes(data.getDay())
        return nomesClases[numeroDoDia]
    }

    function distanciaDesdeDiaUnALuns(data) {
        const dataReferencia = new Date(data)
        const diaUn = new Date(dataReferencia.setDate(1))
        const diaDaSemana = deInicioDomingoAInicioLunes(diaUn.getDay())
        return diaDaSemana
    }

    function dataASemanaDoMes(data) {
        const desfaseSemana = distanciaDesdeDiaUnALuns(data)
        const numeroDiaMes = data.getDate()
        const numeroDaSemana = Math.ceil((numeroDiaMes+desfaseSemana) / 7)
        return "semana"+numeroDaSemana
    }


    
</script>

<div class={"dia "+clases}>
    <span>{diaDoMes}</span>
    <slot/>
</div>

<style>
.dia {
    border: solid white 1px;
    padding: 0.5em 0.5em 0.5em 1em  ;
    position: relative;
    padding-top: 1em;
}
.dia > span {
    position: absolute;
    top: 0;
    left: 0.2em
}
.luns {
    grid-column: 1/2;
}
.martes {
    grid-column: 2/3;
}
.mercores {
    grid-column: 3/4;
}
.xoves {
    grid-column: 4/5;
}
.venres {
    grid-column: 5/6;
}
.sabado {
    grid-column: 6/7;
}
.domingo {
    grid-column: 7/8;
}
.semana1 {
    grid-row: 1/2;
}
.semana2 {
    grid-row: 2/3;
}
.semana3 {
    grid-row: 3/4;
}
.semana4 {
    grid-row: 4/5
}
.semana5 {
    grid-row: 5/6
}
.semana6 {
    grid-row: 6/7
}
</style>