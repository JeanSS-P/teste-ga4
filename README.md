# CRUD (crud-quasar)

GA4

Projeto para gerenciamento de clientes e produtos, aonde existe associação de produtos a cada cliente. No projeto é possível realizar, o cadastro, edição e vinculação de produtos aos clientes. 
O projeto também tem como objetivo principal demonstrar meus conhecimentos utilizando a tecnologia VueJS.

```bash 
TODO:
- Testes unitários
```

## Instalar dependências
```bash
npm install
```

### Iniciar aplicação em modo de desenvolvimento
```bash
npm run dev
```

## Processo de criação do projeto

### Quasar Framework
Optei pela utilização do Quasar pois é uma framework robusta de VueJS que possui uma biblioteca de componentes extensa e variada. O Quasar também faz uma excelente gestão do CSS de forma geral ajudando na montagem de layouts responsivos. O escolhi também principalmente pois possui uma documentação bem escrita/detalhada onde em conjunto com sua grande comunidade é possível encontrar soluções para a maior parte das dúvidas.

### Organização do projeto

#### src/pages
No projeto utilizei mais as estruturas de paginas uma vez que os componentes de formulários de cadastro na sua maioria ou total, eu já conseguia através do Quasar, então não houve necessidade de criação de componentes para atender as necessidades do sistema.

Separei o projeto em 5 páginas totais:

##### Index
Página inicial do projeto
```bash
{ path: '', component: () => import('pages/Index.vue') }
```

##### CadastroCliente
Página de cadastro de cliente
```bash
{ path: 'cliente/criar', component: () => import('pages/cliente/CadastroCliente.vue') },
```

Visão de alteração de cliente
```bash
{ path: 'cliente/:id', component: () => import('pages/cliente/CadastroCliente.vue') },
```

##### CadastroProduto
Página de cadastro de produto
```bash
{ path: 'produto/criar', component: () => import('pages/produto/CadastroProduto.vue') },
```

Visão de alteração de produto
```bash
{ path: 'produto/:id', component: () => import('pages/produto/CadastroProduto.vue') }
```

                        
##### ListaCliente
Listagem de clientes
```bash
{ path: 'cliente', component: () => import('pages/cliente/ListaCliente.vue') },
```

##### ListaProduto
Listagem de produtos
```bash
{ path: 'produto', component: () => import('pages/produto/ListaProduto.vue') },
```

#### src/components

##### ModalAssociadoProdutoCliente
Optei por criar um modal para realizar a associação de produtos aos clientes para que o contexto de associação partisse da listagem do cliente, dando o sentido de execução de uma funcionalidade presente na página de listagem e mantendo o contexto de estar em um local de alterações no cliente.

Realizei a importação do modal no MainLayout, dessa forma criei um acesso global para o modal com objetivo de facilitar a utilização da funcionalidade de associação produto/cliente uma vez que vier a existir a necessidade de realizar esta associação de outro ponto do sistema.

###### ModalConfirmacao
Modal genérico para situações de confirmação

#### src/services
Camada para melhor organização e prover facilidade em possíveis manutenção futuras nos serviços e suas chamadas serviços.

### Organização do arquivo
Organizo os arquivos priorizando as variaveis declaradas primeiro então após o nome do "componente" temos em sequência o (data e computed):
```bash
export default {
  name: 'CadastroCliente',
  data () { return {} },
  computed: {}
},
```

Neste ponto entra os metodos. Nos projetos utilizando Vue2 opto por organizar os metodos em ordem alfabética porque as funções podem ser chamadas em diferentes pontos (No template HTML, dentro de outras funções, em algum Lifecycle do componente, dentro de observadores como o watch, etc..) então prefiro dessa forma para fácil localização em manutenção.

```bash
export default {
  name: 'CadastroCliente',
  data () { return {} },
  computed: {},
  methods: {}
},
```
Em seguida, opto por organizar os Lifecycles do Vue pela ordem de ocorrência:

```bash
export default {
  name: 'CadastroCliente',
  data () { return {} },
  computed: {},
  methods: {},
  beforeCreate () {}, // Por exemplo
  created () {},
  mounted () {}
},
```
Ao final, adiciono as ações realizadas através de um observador (watch):

```bash
export default {
  name: 'CadastroCliente',
  data () { return {} },
  computed: {},
  methods: {},
  beforeCreate () {},
  created () {},
  mounted () {},
  watch: {}
},
```
Existem outros recursos que normalmente declaro ao inicio do script do arquivo como: Mixins, Components, Provide/Inject, entre outros.

### Git Flow

Durante o processo de criação do projeto foi utilizado o fluxo do Git Flow (com exceção durante alguns ajustes para realização do deploy na Vercel).

### Aplicação publicada

Aplicação disponível para visualização em:
https://crud-vue-quasar.vercel.app/
