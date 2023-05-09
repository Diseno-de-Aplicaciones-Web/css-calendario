<script>
    export let data
    $: dataDoEvento = new Date(data)
    $: clases = `${dataADiaDaSemana(dataDoEvento)} ${dataASemanaDoMes(dataDoEvento)}`
    $: diaDoMes = dataDoEvento.getDate()

    function dataADiaDaSemana(data) {
        const nomesClases = ["domingo","luns","martes","mercores","xoves","venres","sabado"]
        const numeroDoDia = data.getDay()
        return nomesClases[numeroDoDia]
    }

    function dataASemanaDoMes(data) {
        const numeroDiaMes = data.getDate()
        const numeroDaSemana = Math.ceil(numeroDiaMes / 7)+1
        return "semana"+numeroDaSemana
    }
    
</script>

<div class={"evento "+clases}>
    <span>{diaDoMes}</span>
    <slot/>
</div>

<style>
div {
    border: solid white 1px;
    padding: 0.5em 0.5em 0.5em 1em  ;
    position: relative;
    padding-top: 1em;
}
div > span {
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
    grid-row: 2/3;
}
.semana2 {
    grid-row: 3/4;
}
.semana3 {
    grid-row: 4/5
}
.semana4 {
    grid-row: 5/6
}
.semana5 {
    grid-row: 6/7
}
.semana6 {
    grid-row: 7/8
}
</style>