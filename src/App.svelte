<script>
  import Calendario from "./lib/Calendario.svelte"
  const eventos = [
    {
      titulo: "Luns",
      data: "2023-05-01",
      prezo: "12,99€"
    },
    {
      titulo: "Martes",
      data: "2023-05-02",
      prezo: "12,99€"
    },
    {
      titulo: "Mercores",
      data: "2023-05-03",
      prezo: "0,50€"
    },
    {
      titulo: "Outro martes",
      data: "2023-05-09",
      prezo: "1000,00€"
    },
    {
      titulo: "Segundo xoves do mes",
      data: "2023-05-11",
      prezo: "1000,00€"
    },
    {
      titulo: "Outra vaca no millo",
      data: "2023-05-11",
      prezo: "1000,00€"
    },
    {
      titulo: "Último día do mes",
      data: "2023-05-31",
      prezo: "1000,00€"
    }
  ]
</script>

<main>
  <Calendario mes={5} ano={2023} eventos={eventos}/>
</main>

<style>
</style>
