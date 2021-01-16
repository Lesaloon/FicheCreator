<template>
	<div class="hello">
		<h1>Lesaloon Fiche Creator</h1>
		<p>
			se site a pour vocation d'aider les étudiant pour crée leur fiche de révision en ligne 
		</p>
		<h3>Matiere</h3>
		<ul>
			<li>
				<p>Nom de la matière</p>
				<input
					type="text"
					name="matiereInput"
					id="MatInp"
					placeholder="Histoire / Françai / Mathematique ..."
					>
			</li>
		</ul>
		<h3>Chapitre</h3>
		<ul>
			<li></li>
			<li></li>
			<li></li>
		</ul>
		<h3>Matiere</h3>
		<h3>Définition</h3>
		<ul>
			<li></li>
			<li></li>
			<li></li>
		</ul>
		<h3>Problematique</h3>
		<ul>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
		</ul>
		<h3>Document externe</h3>
		<ul>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
			<li></li>
		</ul>
	</div>
</template>

<script>
export default {
	name: 'Fiche',
	data() {
		return {
			
		}
	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
	margin: 40px 0 0;
}
ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: inline-block;
	margin: 0 10px;
}
a {
	color: #2980b9;
}
</style>
