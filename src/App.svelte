<script>
  import Calendario from "./lib/Calendario.svelte"
  const eventos = [
    {
      titulo: "Mes anterior, venres",
      data: "2023-03-31",
      prezo: "12,99€"
    },
    {
      titulo: "Día inexistente, ¿lunes?",
      data: "2023-03-32",
      prezo: "12,99€"
    },
    {
      titulo: "Día un, sábado",
      data: "2023-04-01",
      prezo: "12,99€"
    },
    {
      titulo: "Día dous, domingo",
      data: "2023-04-02",
      prezo: "12,99€"
    },
    {
      titulo: "Día tres, luns",
      data: "2023-04-03",
      prezo: "0,50€"
    },
    {
      titulo: "Día nove, domingo",
      data: "2023-04-09",
      prezo: "1000,00€"
    },
    {
      titulo: "Día vintecatro, luns",
      data: "2023-04-24",
      prezo: "1000,00€"
    },
    {
      titulo: "Día 30, domingo",
      data: "2023-04-30",
      prezo: "1000,00€"
    },
    {
      titulo: "Día inexistente, ¿luns?",
      data: "2023-04-31",
      prezo: "1000,00€"
    },
    {
      titulo: "Mes seguinte, luns",
      data: "2023-05-01",
      prezo: "1000,00€"
    },
    {
      titulo: "inexistente 32 de maio, xoves",
      data: "2023-05-32",
      prezo: "1000,00€"
    }

  ]
</script>

<main>
  <h2>marzo 2023</h2>
  <Calendario mes={3} ano={2023} eventos={eventos}/>
  <h2>abril 2023</h2>
  <Calendario mes={4} ano={2023} eventos={eventos}/>
  <h2>maio 2023</h2>
  <Calendario mes={5} ano={2023} eventos={eventos}/>
  <h2>xuño 2023</h2>
  <Calendario mes={6} ano={2023} eventos={eventos}/>
</main>

<style>
</style>
