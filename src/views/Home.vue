<template>

	<div class="home">
		<br>
		<h1>LS créateur de fiche</h1>
		<p>
			Ce site a pour vocation d'aider les étudiants pour créer leur fiche de révision en ligne
		</p>
		<b-form>
			<!-- matière -->
			<b-form-group
				id="input-matiere"
				label="Matière :"
				label-for="input-1"
				description=""
			>
				<b-form-input
					id="input-1"
					v-model="form.matiere"
					type="text"
					required
					placeholder="Entrer le nom de la matière"
				></b-form-input>
			</b-form-group>
			<!-- Chapitre -->
			<b-form-group 
				id="input-chap"
				label="Chapitre : "
				label-for="input-2"
				>
				<p class="left">Numéro : </p>
				<b-form-input
					id="input-2"
					type="number"
					v-model="form.chapitre.num"
					required
					min="0"
				></b-form-input>
				<br>
				<p class="left">Nom : </p>
				<b-form-input
					id="input-2"
					type="text"
					v-model="form.chapitre.nom"
					required
					placeholder="Nom du chapitre"
				></b-form-input>
			
			</b-form-group>
			<!-- problematique -->
			<b-form-group
				id="input-prob"
				label="Problématique :"
				label-for="input-3"
				description=""
			>
				<b-form-textarea
					id="input-3"
					v-model="form.problematique"
					placeholder="La problématique"
				></b-form-textarea>
			</b-form-group>
			<!-- définition -->
			<b-form-group
				id="input-4"
				label="Définition :"
				label-for="input-4"
			>
				<b-form-input
					id="input-4"
					type="text"
					v-model="frommemory.definition.mot"
					placeholder="Mot"
				></b-form-input>
				<br>
				<b-form-textarea
					id="input-4"
					v-model="frommemory.definition.def"
					placeholder="Définition"
				></b-form-textarea>
				<br>
				<b-form-textarea
					id="input-4"
					v-model="frommemory.definition.ex"
					placeholder="Exemple"
				></b-form-textarea>
				<br>
				<b-button v-on:click="addDef()" variant="success">Ajouter la définition</b-button>
			</b-form-group> 
			<!-- définition Liste -->
			<b-list-group v-for="(element, index) in form.définition" :key="'def'+index" class="left color">
				<b-list-group-item>
					{{element.mot}} : {{element.def}}
					<b-button class="align-right" variant="danger" v-on:click="suprDef(index)">Supprimer</b-button>
					<br>
					<span style="padding-left: 20px;" >EX : {{element.ex}}</span>
				</b-list-group-item>
			</b-list-group> 
			<!-- shema 
			<b-form-group
				id="input-5"
				label="Schéma :"
				label-for="input-5"
			>
				<b-form-input
					id="input-5"
					type="text"
					v-model="frommemory.schema.link"
					placeholder="Lien de l'image"
				></b-form-input>
				<br>
				<b-form-textarea
					id="input-5"
					v-model="frommemory.schema.nom"
					placeholder="Nom"
				></b-form-textarea>
				<br>
				<b-form-textarea
					id="input-5"
					v-model="frommemory.schema.type"
					placeholder="Type de document"
				></b-form-textarea>
				<br>
				<b-button v-on:click="addShema()" variant="success">Ajouter la définition</b-button>
			</b-form-group>
			<br>-->
			<!-- shema Liste 
			<b-list-group v-for="(element, index) in form.schema" :key="'shema'+index" class="left color">
				<b-list-group-item>
					{{element.link}} : {{element.type}}
					<b-button class="align-right" variant="danger" v-on:click="suprShema(index)">Supprimer</b-button>
					<br>
					<span style="padding-left: 20px;" >type : {{element.type}}</span>
					
				</b-list-group-item>
			</b-list-group> -->
			<!-- Vocabulaire -->
			<b-form-group
				id="input-6"
				label="Vocabulaire :"
				label-for="input-5"
			>
				<b-form-input
					id="input-6"
					type="text"
					v-model="frommemory.vocabulaire.mot"
					placeholder="Mot"
				></b-form-input>
				<br>
				<b-form-textarea
					id="input-6"
					v-model="frommemory.vocabulaire.signification"
					placeholder="Signification"
				></b-form-textarea>
				<br>
				<b-button v-on:click="addVoc()" variant="success">Ajouter le vocabulaire</b-button>
			</b-form-group> 
			<br>
			<b-list-group v-for="(element, index) in form.vocabulaire" :key="'vocabulaire'+index" class="left color">
				<b-list-group-item>
					{{element.mot}}
					<b-button class="align-right" variant="danger" v-on:click="suprVoc(index)">Supprimer</b-button>
					<br>
					<span style="padding-left: 20px;" >{{element.signification}}</span>
					
				</b-list-group-item>
			</b-list-group> <!-- Vocabulaire Liste -->
			<br>
			
			<!-- proprieter -->
			<b-form-group
				id="input-6"
				label="proprieter :"
				label-for="input-6"
			>
				<b-form-textarea
					id="input-6"
					v-model="frommemory.proprieter.prop"
					placeholder="Propriété"
				></b-form-textarea>
				<br>
				<b-button v-on:click="addProp()" variant="success">Ajouter la propriété</b-button>
			</b-form-group> 
			<br>
			<b-list-group v-for="(element, index) in form.proprieter" :key="'proprieter'+index" class="left color">
				<b-list-group-item>
					{{element.prop}}
					<b-button class="align-right" variant="danger" v-on:click="suprProp(index)">Supprimer</b-button>
					
				</b-list-group-item>
			</b-list-group> <!-- proprieter Liste -->
			<br>
			<!-- définition -->
			<b-form-group
				id="input-4"
				label="Document externe :"
				label-for="input-4"
			>
				<b-form-input
					id="input-4"
					type="number"
					v-model="frommemory.document.page"
					placeholder="Page"
				></b-form-input>
				<br>
				<b-form-input
					id="input-4"
					type="number"
					v-model="frommemory.document.doc"
					placeholder="Document numero"
				>
				</b-form-input>
				<br>
				<b-form-textarea
					id="input-4"
					v-model="frommemory.document.nom"
					placeholder="Nom du document"
				></b-form-textarea>
				<br>
				<b-button v-on:click="addDoc()" variant="success">Ajouter la définition</b-button>
			</b-form-group> 
			<!-- définition Liste -->
			<b-list-group v-for="(element, index) in form.document" :key="'doc'+index" class="left color">
				<b-list-group-item>
					Le Document {{element.doc}} page {{element.page}} : {{element.nom}}
					<b-button class="align-right" variant="danger" v-on:click="suprDoc(index)">Supprimer</b-button>
					<br>
					
				</b-list-group-item>
			</b-list-group>

			<br>
			
			<b-button variant="primary" v-on:click="CreatePDF">Sauvegarder le PDF</b-button>
			<br>
			<br>
			<b-button type="reset"	variant="danger" >Reset</b-button>
		</b-form>

		<b-card class="mt-3" header="Le Json" headerClass="cardHeader">
			<pre class="m-0" style="text-align: left">{{ form }}</pre>
		</b-card>
		<br>
		<!--<h3>Matiere</h3>
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
		<h3>Matière</h3>
		<h3>Définition</h3>
		<ul>
			<li></li>
			<li></li>
			<li></li>
		</ul>
		<h3>Problématique</h3>
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
		</ul>-->
	</div>
</template>

<script>
var pdfMake = require('pdfmake/build/pdfmake.js');
var font = require('pdfmake/build/vfs_fonts.js');

//var pdfFonts = require('pdfmake/build/vfs_fonts.js');
Array.prototype.remove = function(from, to){
  this.splice(from, (to=[0,from||1,++to-from][arguments.length])<0?this.length+to:to);
  return this.length;
};
export default {
	name: 'Home',
	data() {
		return {
			frommemory: {
				definition: {
					mot: "",
					def: "",
					ex : ""
				},
				schema: {
					link: "",
					nom : "",
					type: ""
				},
				vocabulaire: {
					mot				: "",
					signification	: ""
				},
				proprieter : {
					prob: ""
				},
				document: {
					page : '',
					doc : '',
					nom : ''
				}
			},
			form: {
					matiere: '',
					chapitre: {
						num : '1',
						nom : ""
					},
					problematique: "",
					définition: [
						/*{
						"mot": "aze",
						"def": "aze",
						"ex": "aze"
						}*/
					],
					schema: [],
					vocabulaire: [],
					proprieter: [],
					document: [
							/*{
									page : '0',
									doc : '-1',
									nom : ''
							}*/
					]
			}
		}
	},
	methods : {
		CreatePDF: function() {
			var tempDef = []
			this.form.définition.forEach(element => {
				tempDef.push({ text: `${element.mot} : ${element.def}\nex : ${element.ex}`, style: 'def' })
			});
			var tempShe = []
			/*this.form.schema.forEach(element => {
				tempShe.push({ text: `${element.mot} : ${element.def}\nex : ${element.ex}`, style: 'def' })
			});*/
			var tempVoc = []
			this.form.vocabulaire.forEach(element => {
				tempVoc.push({ text: `${element.mot} : ${element.signification}`, style: 'def' })
			});
			var tempProp = []
			this.form.proprieter.forEach(element => {
				tempDef.push({ text: `${element.prob}`, style: 'def' })
			});

			var tempDoc = []
			this.form.document.forEach(element => {
				tempDoc.push({ text: `Document : ${element.doc} page : ${element.page}\nNom : ${element.nom}`, style: 'def' })
			});
			var docDefinition = {
				content: [
					{ text: `${this.form.matiere}`, style: 'header' },
					{ text: `Chapitre ${this.form.chapitre.num} : ${this.form.chapitre.nom}`, style: 'header' },
					{ text: `${this.form.problematique}`, style: 'problematique' },

					{ text: `${tempDef.length > 0 ? "Définition : ": ""}`, style: 'problematique' },
					{
						ul: tempDef
					},
					{ text: `${tempShe.length > 0 ? "Schéma : ": ""}`, style: 'problematique' },
					{
						ul: tempShe
					},/*
					{ text: `${tempVoc.length > 0 ? "Vocabulaire : ": ""}`, style: 'problematique' },
					{
						ul: tempVoc
					},*/
					{ text: `${tempProp.length > 0 ? "Propriété : ": ""}`, style: 'problematique' },
					{
						ul: tempProp
					},
					{ text: `${tempDoc.length > 0 ? "Document : ": ""}`, style: 'problematique' },
					{
						ul: tempDoc
					}
				],
				styles: {
					def: {
						fontSize: 12,
						bold: false,
						alignment: 'left'
					},
					title: {
						fontSize: 18,
						bold: true,
						decoration: "underline"
					},
					header: {
						fontSize: 20,
						bold: true,
						alignment: 'center',
						decoration: "underline"
					},
					problematique: {
						fontSize: 12,
						margin: 10,
						bold: true,
					},
					anotherStyle: {
						italics: true,
						alignment: 'right'
					}
				}
			}
			
			pdfMake.vfs = font.pdfMake.vfs
			pdfMake.createPdf(docDefinition).open();

		},


		addDef: function() {
			this.form.définition.push(this.frommemory.definition)
			this.frommemory.definition = {
				mot: "",
				def: "",
				ex : ""
			}
		},
		suprDef: function(index) {
			(this.form.définition).remove(index)
		},
		addShema: function() {
			console.log(this.form);
			this.form.schema.push(this.frommemory.schema)
			this.frommemory.schema = {
				mot: "",
				def: "",
				ex : ""
			}
		},
		suprShema: function(index) {
			console.log(index);
			console.log(this.form);
			(this.form.schema).remove(index)
		},
		addVoc: function() {
			console.log(this.form);
			this.form.vocabulaire.push(this.frommemory.vocabulaire)
			this.frommemory.vocabulaire = {
				mot: "",
				signification: ""
			}
		},
		suprVoc: function(index) {
			(this.form.vocabulaire).remove(index)
		},
		addProp: function() {
			console.log(this.form);
			this.form.proprieter.push(this.frommemory.proprieter)
			this.frommemory.proprieter = {
				prop: ""
			}
		},
		suprProp: function(index) {
			(this.form.proprieter).remove(index)
		},
		addDoc: function() {
			console.log(this.form);
			this.form.document.push(this.frommemory.document)
			this.frommemory.document = {
				page : '',
				doc : '',
				nom : ''
			}
		},
		suprDoc: function(index) {
			(this.form.document).remove(index)
		}
	}
}
</script>

<style scoped>
.align-right {
	float:right;
}
.left {
	text-align: left;
}
.color {
	color:  #2c3e50;
}
.home {
	width: 60%;
	margin: 0 auto;
	background-color: #2c3e50;;
}
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
.cardHeader {
	color: #2c3e50;
}

@media only screen and (max-width: 1000px) {
  .home {
    width: 80%;
  }
}
</style>
