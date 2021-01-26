# Curso para iniciantes da [FreeCodeCamp](https://www.freecodecamp.org/)

* [Link do curso](https://www.youtube.com/watch?v=4deVCNJq3qc&t=6s)
* [VueJS](https://vuejs.org/)

# Anotações

## Instancia VueJS

    new Vue ({

    })

* **el** --> Que elemento no DOM queremos afetar com a instância Vue.

    new Vue ({
        el: "#root"       
    })

* **data** --> Objeto que usamos para popularizar variáveis para que podemos usar no DOM.
    new Vue ({
        el: "#root",
        data: {
            greeting: 'Hello vue',
        }        
    })

* **OBS:** {{  }} a sintaxe do bigode duplo é utilizada para usar código JavaScript no template.

## Data Binding

* Vue possui uma ligação de dados de duas vias, ou seja, se você modificar um dado em uma delas, a outra será modificada também.

#### v-model

* <'input v-model="greeting"> --> Liga o valor da data variável greeting ao input.

#### v-if

* <'div v-if="count === 1">Green</'div> --> É literalmente uma condicional. Só irá renderizar o elemento se ele cumprir a condicional que está inserida dentro da diretiva v-if;

#### v-else-if

* <'div v-else-if="count === 2">Red</'div> ---> Condicional que é realizada caso a primeira não seja.

#### v-else

* <'div v-else>Orange</'div> ---> Caso nenhuma das condicionais acima sejam satisfeitas.

#### v-show

* <'div v-show="count === 1">Orange</'div>;
* No caso do v-show, se a condição não for satisfeita, o elemento ainda irá ser renderizado na tela porém com um display: none.

#### v-bind

* Chaves duplas não pódem ser usadas em atributos HTML, para isso, utilizamos a diretiva v-bind;
* <'div v-bind:id="elementID"></'div>;
* <'button v-bind:disabled="email.length < 2"></'button>
* Também pode ser escrito da seguinte maneira: :class (v-bind:class)

#### v-text

* Para colocar textos em um elemento HTML.

#### v-html

* Colocar textos dentro de um elemento HTML porém, aceita inserir esses textos como se fossem elementos HTML.

#### v-once 

* Renderiza o elemento na tela apenas uma vez, no seu estado inicial.

#### v-for

* Laço em forma de diretiva;
* <'li v-for="cat in cats">{{ cat }}</'li>

#### v-on

* Diretivas para eventos;
* v-on:click="functionName" ou @click="functionName";
* @keyup.enter --> Realiza a função addKitty quando você pressionar a tecla enter.

## methods

* O objeto data é usado para guardar variáveis, logo, precisamos de um objeto para guardar nossas funções. Este objeto é o methods.

app = new Vue({
	el: '#root',
  data: {
		cats: [
    	{name: "kitkat"},
      {name: 'henry'},
      {name: 'bosco'},
      {name: 'fish'},
    ],
    newCat: '',
  },
  methods: {
  	addKitty() {
    	this.cats.push({name: this.newCat})
      this.newCat = ''
    },
  },
})

## filters

* O Vue permite que você defina filtros que podem ser utilizados para aplicação de formatações de texto corriqueiras;
* Filtros são permitidos em interpolações, mustache e expressões v-bind.

app = new Vue({
    el: '#root',
  data: {
		cats: [
    	{name: "kitkat"},
      {name: 'henry'},
      {name: 'bosco'},
      {name: 'fish'},
    ],
    newCat: '',
  },
  filters: {
  	capitalize(value) {
    	return value.toUpperCase()
    },
    kittify(value) {
			return value + "y"
    }
  }
})

## computed

* Formatações com lógicas.
app = new Vue({
	el: '#root',
  data: {
		cats: [
    	{name: "kitkat"},
      {name: 'henry'},
      {name: 'bosco'},
      {name: 'fish'},
    ],
    newCat: '',
  },
  methods: {
  	addKitty() {
    	this.cats.push({name: this.newCat})
      this.newCat = ''
    },
  },
  filters: {
  	capitalize(value) {
    	return value.toUpperCase()
    },
    kittify(value) {
			return value + "y"
    }
  }
})

## Componentes

Vue.component('cat-list', {
	props: ['cats'],
	template:` 
  	<ul>
    	<li v-for="cat in cats">{{ cat.name }}</li>
    </ul
  `
})