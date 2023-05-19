<input type="text" bind:value={query} />

<script>
    import users from "./users.json"
    let query = ""

    // Only include results that begin with the query, sorted by rank
    $: results = users.filter(user => user.user.startsWith(query)).sort((a, b) => a.rank - b.rank).map(user => ({...user, rank: user.rank + 1}))
</script>

<table>
    <tr>
        <th>Rank</th>
        <th>User</th>
        <th>Score</th>
    </tr>
    {#each results.slice(0, 100) as user}
        <tr>
            <td>{user.rank}</td>
            <td><a href="https://eksisozluk1923.com/biri/{user.user}" target="_blank">{user.user}</a></td>
            <td>{user.score}</td>
        </tr>
    {/each}
</table>


<style>
    input {
        width: 500px;
        padding: 10px;
        font-size: 16px;
        border: 1px solid #ccc;
    }
</style>