<script>
import Dashboard from "../components/Dashboard.svelte";
import Header from "../components/Header.svelte";
import {v4} from 'uuid';


	let notes = [
		{
			id: 0,
			title: 'Vacaciones',
			color: 'yellow',
			text: 'Hola'
		},
		{
			id: 0,
			title: 'Vacaciones',
			color: 'red',
			text: 'Hola Jaime'
		}
	];
	let copyNotes = [ ...notes];

	$: count = notes.length;
	
	function handleNew() {
		const color = generateColor();
		const id = v4();
		const note = {
			id: id,
			title: '',
			color: color,
			text: ''
		};
		notes =[note, ...notes];
		copyNotes = [...notes];
	}
	function generateColor(){
		const colors = ['#DDFFC2','#FFC2C2', '#FFEAC2', '#C2FFD3', '#C2FFEC', '#C2E2FF', '#CBC2FF', '#EBC2FF', '#FFC2F7', '#FFC2D8'];
		const index = Math.floor(Math.random() * (colors.length));
		return colors[index];
	}

	function handleUpdate(e){
		const note = e.detail;
		const index = notes.findIndex(n => n.id === note.id);
		notes[index] = note;
		copyNotes = [...notes];
	}

</script>

<main>
	<Header/>
	<div class="count-notes">{count} notas</div>
	<Dashboard notes={notes} on:click={handleNew} on:update={handleUpdate}/>
</main>

<style>
	:global(body){
		margin: 0;
		padding: 0;
	}
	.count-notes{
		padding: 20px 20px 0 20px;
		text-align: right;
	}
</style>