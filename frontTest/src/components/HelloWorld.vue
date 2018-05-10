<template>
  <v-app>
    <div>
      <v-btn @click="criarModal()" color="primary"> Criar </v-btn>
      <v-btn color="primary"> Editar </v-btn>
      <v-data-table
      :headers="headers"
      :items="itens1"
      hide-actions
      class="theme--light"
      >
        <template slot="items" slot-scope="props">
          <tr @click="contextoModal(props.item)">
            <td>{{ props.item.nome }}</td>
            <td>{{ props.item.descricao }}</td>
            <td>{{ props.item.tipo }}</td>
            <td>{{ props.item.nomeResponsavel }}</td>
            <td>{{ props.item.tipoIntegracao }}</td>
          </tr>
      </template>
      </v-data-table>
    </div>
    <!-- Cadastro de Novo M1 -->
    <v-dialog v-model="createDialog" @keydown.esc="createDialog = false" max-width="790">
      <v-card>
        <form v-on:submit="handleSubmit($event)">
        <v-card-title style="background-color: #4251AE; color:white;">
          <h3>Criar um usuário</h3>
        </v-card-title>
        <v-card-text>
          <v-text-field
            label="Nome de usuário"
            v-model="cadastroNovoItens1.nome"
            required
            >
          </v-text-field>
          <v-text-field
            label="descricao"
            v-model="cadastroNovoItens1.descricao"
            required
            >
          </v-text-field>
          <v-text-field
            label="tipo"
            v-model="cadastroNovoItens1.tipo"
            required
            >
          </v-text-field>
          <v-text-field
            label="nome do responsável"
            v-model="cadastroNovoItens1.nomeResponsavel"
            required
          >
          </v-text-field>
          <v-text-field
            label="Tipo de integração"
            v-model="cadastroNovoItens1.tipoIntegracao"
            required
            >
          </v-text-field>
        </v-card-text>
        <v-card-actions>
          <v-btn  class="green white--text" style="margin-bottom:20px" block @click="buscarM1(), createDialog=false, cadastrarM1()"><i style="margin-right:10px" class="material-icons">save</i>Cadastrar</v-btn>
          <v-btn class="red white--text" style="margin-bottom:20px" block  @click.stop="userCreateDialog = false "><i style="margin-right:10px" class="material-icons">close</i>Fechar</v-btn>
        </v-card-actions>
        </form>
      </v-card>
    </v-dialog>
<!-- editar M1 -->
    <v-dialog v-model="editarDialog" @keydown.esc="editarDialog = false" persistent max-width="690">
      <v-card>
        <form>
          <v-text-field
            v-model="m1Editado.nome"
            label="Nome"
            required
          ></v-text-field>
          <v-text-field
            v-model="m1Editado.descricao"
            label="Descrição"
            required
          ></v-text-field>
          <v-text-field
            v-model="m1Editado.tipo"
            label="Tipo"
            required
          ></v-text-field>
          <v-text-field
            v-model="m1Editado.nomeResponsavel"
            label="Nome do responsável"
            required
          ></v-text-field>
          <v-text-field
            v-model="m1Editado.tipoIntegracao"
            label="E-Tipo de integração"
            required
          ></v-text-field>
          <v-card-actions>
            <v-btn  @click="editarModal(dadosModal)">submit</v-btn>
            <!-- <v-btn @click="clear">clear</v-btn> -->
            <v-spacer></v-spacer>
            <v-btn color="primary" >Fechar</v-btn>
          </v-card-actions>
        </form>
      </v-card>
    </v-dialog>
  </v-app>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      createDialog: false,
      editarDialog: false,
      headers: [
        { text: 'Nome', value: 'nome' },
        { text: 'Descricao', value: 'descricao' },
        { text: 'Tipo', value: 'tipo' },
        { text: 'Nome do responsável', value: 'nomeResponsavel' },
        { text: 'tipo de integracao', value: 'tipoIntegracao' }
      ],
      cadastroNovoItens1: {
        nome: '',
        descricao: '',
        tipo: '',
        nomeResponsavel: '',
        tipoIntegracao: ''
      },
      m1Editado: {
        nome: '',
        descricao: '',
        tipo: '',
        nomeResponsavel: '',
        tipoIntegracao: ''
      },
      itens1: [
        { nome: 'a1',
          descricao: 'a2',
          tipo: 'a3',
          nomeResponsavel: 'a4',
          tipoIntegracao: 'a5'
        },
        { nome: 'b1',
          descricao: 'b2',
          tipo: 'b3',
          nomeResponsavel: 'b4',
          tipoIntegracao: 'b5'
        },
        { nome: 'c1',
          descricao: 'c2',
          tipo: 'c3',
          nomeResponsavel: 'c4',
          tipoIntegracao: 'c5'
        },
      ],
    }
  },
  methods: {
    criarModal () {
      this.createDialog = true
    },
    cadastrarM1 () {
      console.log('Na teoria seu coiso foi cadastrado, mas essa função não faz nada, contudo, ela está aqui pra não gerar erro na minha telinha')
    },
    editarModal () {
      console.log('vamos fingir que os dados foram editados')
      this.editarDialog = false
    },
    contextoModal (m1) {
      this.dadosModal = m1
      this.editarDialog = true
    },
    buscarM1 () {
      console.log('quando cadastrado o usuário, ele chamará a função de buscar :D')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
