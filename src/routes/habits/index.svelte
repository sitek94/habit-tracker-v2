<script>
  import { addDays, eachDayOfInterval, format, isWeekend, previousMonday } from 'date-fns'

  const start = previousMonday(new Date())
  const days = eachDayOfInterval({
    start,
    end: addDays(start, 13)
  })

</script>

<svelte:head>
	<title>Todos</title>
</svelte:head>

<div>
	<h1>Habits</h1>

  <table>
    <thead>
      <tr>
        {#each days as day}
          <th class:weekend={isWeekend(day)}>{format(day, 'EEEEEE')}</th>
        {/each}
      </tr>
    </thead>
    <tbody>
      <tr>
        <td colspan={14}>
          Get up 5am
        </td>
      </tr>
      <tr>
        {#each days as day}
          <td>
            <input type="checkbox" />
          </td>
        {/each}
      </tr>
    </tbody>
  </table>
</div>

<style>
  th {
    font-weight: normal;
  }

  th.weekend {
    font-weight: bold;
  }

  table {
    border-collapse: collapse;
  }
  table, th, td {
    border: 1px solid;
  }

  input[type='checkbox'] {
    width: 20px;
    height: 20px;
  }
</style>
