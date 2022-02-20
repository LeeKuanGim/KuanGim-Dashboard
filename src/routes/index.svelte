<script>
    import supabase from '$lib/db';

    async function signOut() {
   	 const { error } = await supabase.auth.signOut();

   	 if (error) alert(error.message); // alert if error
    }

    let timetable = {
	Monday: [
  	{
    	name: "PH",
    	period: 1,
    	style: "",
  	},
  	{
    	name: "PM",
    	period: 1,
    	style: "",
  	},
  	{
    	name: "BI",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "R",
    	period: 1,
    	style: "table-success",
  	},
  	{
    	name: "BM",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "M3",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "BC",
    	period: 2,
    	style: "",
  	},
	],
	Tuesday: [
  	{
    	name: "PJPK",
    	period: 1,
    	style: "",
  	},
  	{
    	name: "M3",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "BI",
    	period: 1,
    	style: "",
  	},
  	{
    	name: "E",
    	period: 1,
    	style: "table-success",
  	},
  	{
    	name: "BM",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "BC",
    	period: 3,
    	style: "",
  	},
  	{
    	name: "PJPK",
    	period: 1,
    	style: "",
  	},
	],
	Wednesday: [
  	{
    	name: "BC",
    	period: 3,
    	style: "",
  	},
  	{
    	name: "PM",
    	period: 1,
    	style: "",
  	},
  	{
    	name: "H",
    	period: 1,
    	style: "table-success",
  	},
  	{
    	name: "PKS",
    	period: 3,
    	style: "",
  	},
  	{
    	name: "BM",
    	period: 2,
    	style: "",
  	},
	],
	Thursday: [
  	{
    	name: "SA",
    	period: 1,
    	style: "",
  	},
  	{
    	name: "PJPK",
    	period: 1,
    	style: "",
  	},
  	{
    	name: "BM",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "A",
    	period: 1,
    	style: "table-success",
  	},
  	{
    	name: "PM",
    	period: 1,
    	style: "",
  	},
  	{
    	name: "BC",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "M3",
    	period: 2,
    	style: "",
  	},
	],
	Friday: [
  	{
    	name: "BI",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "BM",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "T",
    	period: 1,
    	style: "table-success",
  	},
  	{
    	name: "BC",
    	period: 2,
    	style: "",
  	},
  	{
    	name: "PM",
    	period: 1,
    	style: "",
  	},
  	{
    	name: "SA",
    	period: 2,
    	style: "",
  	},
	],
  };
  function addTimeSlot(day){
  	if(day=="Monday"){
		timetable.Monday = [
    ...timetable.Monday,
    { name: "??", period: 1, style: "" }
  ];
 	}
  	else if(day=="Tuesday"){
		timetable.Tuesday = [
    ...timetable.Tuesday,
    { name: "??", period: 1, style: "" }
  ];
  	}
  	else if(day=="Wednesday"){
		timetable.Wednesday = [
    ...timetable.Wednesday,
    { name: "??", period: 1, style: "" }
  ];
  	}
  	else if(day=="Thursday"){
		timetable.Thursday = [
    ...timetable.Thursday,
    { name: "??", period: 1, style: "" }
  ];
  	}
  	else{
		timetable.Friday = [
    ...timetable.Friday,
    { name: "??", period: 1, style: "" }
  ];
  	}
  }

  	let curDay;
	let curIndex;
	let curName;
	let curPeriod;
	let curStyle;

	function showCurData(day,index,name,period,style){
		curDay=day;
		curIndex=index;
		curName=name;
		curPeriod=period;
		curStyle=style;
	}
</script>

<h1>My Dashboard</h1>
<h7>School Timetable</h7>

<table class="table table-bordered text-center ">
    <thead>
      <!--for the first row-->
      <tr>
        <th scope="col">#</th>
        <th scope="col">1</th>
        <th scope="col">2</th>
        <th scope="col">3</th>
        <th scope="col">4</th>
		    <th scope="col">-</th>
        <th scope="col">5</th>
        <th scope="col">6</th>
        <th scope="col">7</th>
        <th scope="col">8</th>
        <th scope="col">9</th>
        <th scope="col">10</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th scope="row">Monday</th>
        {#each timetable.Monday as timeSlot,index}
          <td colspan={timeSlot.period} class={timeSlot.style}>
          <button class="btn" type="button" data-bs-toggle="modal" data-bs-target="#editTimeSlot" on:click={() =>
            	showCurData(
              	"Monday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
>{timeSlot.name}</button>
          </td>
        {/each}
			<td class="btn" on:click={() => addTimeSlot("Monday") }>+</td>
      </tr>
      <tr>
        <th scope="row">Tuesday</th>
        {#each timetable.Tuesday as timeSlot,index}
          <td colspan={timeSlot.period} class={timeSlot.style}>
          <button class="btn" type="button" data-bs-toggle="modal" data-bs-target="#editTimeSlot" on:click={() =>
            	showCurData(
              	"Tuesday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
>{timeSlot.name}</button>
          </td>
        {/each}
			<td class="btn" on:click={() => addTimeSlot("Tuesday")}>+</td>
      </tr>
      <tr>
        <th scope="row">Wednesday</th>
        {#each timetable.Wednesday as timeSlot,index}
          <td colspan={timeSlot.period} class={timeSlot.style}>
          <button class="btn" type="button" data-bs-toggle="modal" data-bs-target="#editTimeSlot" on:click={() =>
            	showCurData(
              	"Wednesday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
>{timeSlot.name}</button>
          </td>
        {/each}
			<td class="btn" on:click={() => addTimeSlot("Wednesday")}>+</td>
      </tr>
      <tr>
        <th scope="row">Thursday</th>
        {#each timetable.Thursday as timeSlot,index}
          <td colspan={timeSlot.period} class={timeSlot.style}>
          <button class="btn" type="button" data-bs-toggle="modal" data-bs-target="#editTimeSlot" on:click={() =>
            	showCurData(
              	"Thursday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
>{timeSlot.name}</button>
          </td>
        {/each}
			<td class="btn" on:click={() => addTimeSlot("Thursday")}>+</td>
      </tr>
      <tr>
        <th scope="row">Friday</th>
        {#each timetable.Friday as timeSlot,index}
          <td colspan={timeSlot.period} class={timeSlot.style}>
          <button class="btn" type="button" data-bs-toggle="modal" data-bs-target="#editTimeSlot" on:click={() =>
            	showCurData(
              	"Friday",
              	index,
              	timeSlot.name,
              	timeSlot.period,
              	timeSlot.style
            	)}
>{timeSlot.name}</button>
          </td>
        {/each}
			<td class="btn" on:click={() => addTimeSlot("Friday")}>+</td>
      </tr>
    </tbody>
  </table>

 
  

<!-- Sign Out -->
<section class="container px-4 py-3 text-center">
    <button class="btn btn-secondary" on:click={signOut}>Logout</button>
</section>



<!-- Modal -->
<div class="modal fade" id="editTimeSlot" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="staticBackdropLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="staticBackdropLabel">Edit Time Slot</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <div class="input-group mb-3">
  <span class="input-group-text" id="basic-addon1">Name</span>
  <input type="text" class="form-control"  aria-label="Username" aria-describedby="basic-addon1" bind:value={curName}>
</div>
<div class="input-group mb-3">
  <span class="input-group-text" id="basic-addon1">Period</span>
  <input type="number" class="form-control"  aria-label="Username" aria-describedby="basic-addon1" bind:value={curPeriod}>
</div>
<div class="input-group mb-3">
  <span class="input-group-text" id="basic-addon1">Style</span>
  <select class="form-select" id="inputGroupSelect01" bind:value={curStyle}>
    <option selected value="">Default</option>
    <option value="table-primary">Blue</option>
    <option value="table-success">Green</option>
    <option value="table-danger">Red</option>
	<option value="table-warning">Yellow</option>
	<option value="table-secondary">Grey</option>
  </select>
  

</div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>