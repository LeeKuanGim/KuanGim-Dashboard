<script>
    import Greeting from '$lib/Greeting.svelte';
    import Entry from '$lib/Entry.svelte';
    import EntryModal from '$lib/EntryModal.svelte';
    import supabase from '$lib/db';

    async function signOut() {
   	 const { error } = await supabase.auth.signOut();

   	 if (error) alert(error.message); // alert if error
    }

    // Select entries
    async function getEntries() {
   	 const { data, error } = await supabase.from('moodEntries').select();
   	 if (error) alert(error.message);

   	 return data;
    }
</script>
<h1>My Dashboard</h1>
<h5>My School Timetable</h5>
<table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">1</th>
      <th scope="col">2</th>
      <th scope="col">3</th>
      <th scope="col">4</th>
      <th scope="col">5</th>
      <th scope="col">6</th>
      <th scope="col">7</th>
      <th scope="col">8</th>
      <th scope="col">9/th>
      <th scope="col">10</th>
      <th scope="col">11</th>
      <th scope="col">12</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">MON</th>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th scope="row">TUE</th>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th scope="row">WED</th>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th scope="row">THU</th>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th scope="row">FRI</th>
      <td></td>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>
<Greeting />
<!--   Entries   -->
<section class="container px-4 py-3">
    <div class="d-flex justify-content-between">
   	 <div class="p-2">Mood Log</div>
   	 <input
   		 class="btn btn-light mb-2"
   		 type="button"
   		 value="+ New Entry"
   		 data-bs-toggle="modal"
   		 data-bs-target="#newEntry"
   	 />
    </div>

    <div class="list-group mb-3">
   	 <!-- Individual Entries -->
   	 {#await getEntries()}
   		 <p>Fetching data...</p>
   	 {:then data}
   		 {#each data as entry}
   			 <Entry
   				 date={entry.day + '-' + entry.month + '-' + entry.year}
   				 mood={entry.mood}
   				 comment={entry.comment}
   			 />
   		 {/each}
   	 {:catch error}
   		 <p>Something went wrong while fetching the data:</p>
   		 <pre>{error}</pre>
   	 {/await}
    </div>
</section>

<!-- Sign Out -->
<section class="container px-4 py-3 text-center">
    <button class="btn btn-secondary" on:click={signOut}>Logout</button>
</section>

<EntryModal />