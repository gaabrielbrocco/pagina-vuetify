<template>
  <v-app theme="dark">
    <v-navigation-drawer v-model="isDrawerOpen">
      <v-list>
        <v-list-subheader>Menu</v-list-subheader>

          <v-list-item prepend-icon="mdi-home" href="google.com">Home</v-list-item>

          <v-list-item prepend-icon="mdi-account" href="google.com" title="Perfil"></v-list-item>


        <v-list-group value="Clientes">
          <template #activator="{ props }">
            <v-list-item
              v-bind="props"
              prepend-icon="mdi-account-circle"
              title="Clientes"
            ></v-list-item>
          </template>
          
          <v-list-item href="google.com" prepend-icon="mdi-currency-usd">Faturamento</v-list-item>
          <v-list-item href="google.com" prepend-icon="mdi-chart-line">Relatório</v-list-item>

        </v-list-group>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar flat class="border-b">
      <v-app-bar-nav-icon @click="isDrawerOpen = !isDrawerOpen" ></v-app-bar-nav-icon>
      <v-app-bar-title>Meu app</v-app-bar-title>

      <template #append>
        <v-btn icon class="mr-3">
          <v-badge content="22" color="warning">
            <v-icon icon="mdi-bell-outline"></v-icon>
          </v-badge>
        </v-btn>
          
          <v-menu>
            <template #activator="{ props }">
              <v-avatar v-bind="props">
                <v-img
                  cover 
                  src="https://cdn.media.amplience.net/i/partycity/278696?$large$&fmt=auto&qlt=default"></v-img>
              </v-avatar>
            </template>

            <v-card min-width="200px">
              <v-list :lines="false" density="compact" nav>
                <v-list-item prepend-icon="mdi-account-outline">
                  <v-list-item-title>Meu Perfil</v-list-item-title>
                </v-list-item>
                <v-list-item prepend-icon="mdi-heart-outline">
                  <v-list-item-title>Favoritos</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-card>
          </v-menu>
      </template>
    </v-app-bar>

    <v-main>
      <v-container >
        <h1 class="mb-6">Dashboard</h1>

        <v-card flat class="border mb-4">
          <div class="d-flex justify-space-between">
            <v-card-title>Últimos usuários</v-card-title>

            <v-card-title>
              <v-btn @click="isDialogOpen = true" variant="tonal" size="small">Adicionar usuário</v-btn>
              
              <v-dialog 
                width="600px"
                v-model="isDialogOpen"
              >
                <v-card>
                  <v-card-title>Adicionar usuário</v-card-title>
                  <v-card-text>
                    <v-row>
                        <v-col>
                          <v-text-field 
                            label="Nome" 
                            variant="outlined"
                          >
                          </v-text-field>
                        </v-col>

                        <v-col>
                          <v-text-field 
                            label="Email" 
                            variant="outlined"
                            :rules="emailRules"
                          >
                          </v-text-field>
                        </v-col>
                    </v-row>

                    <v-select 
                      label="Cargo" 
                      variant="outlined"
                      :items="['Administrador', 'Gerente','Convidado']"
                    >
                    </v-select>
                  </v-card-text>

                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn variant="text" @click="isDialogOpen = false">Cancelar</v-btn>
                    <v-btn variant="tonal" color="success">Salvar</v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>   
            </v-card-title>         
          </div>
          <v-table>
                <thead>
                  <tr>
                    <th>Nome</th>
                    <th>E-mail</th>
                    <th>Cargo</th>
                    <th>Ações</th>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <td>Fulano</td>
                    <td>fulano@gmail.com</td>
                    <td>
                      <v-chip color="primary" variant="outlined" size="small">Administrador</v-chip>
                    </td>
                    <td>
                      <v-btn variant="tonal">Editar</v-btn>
                    </td>
                  </tr>
                  <tr>
                    <td>Beltrano</td>
                    <td>beltrano@yahoo.com.br</td>
                    <td>
                      <v-chip color="success" variant="outlined" size="small">Gerente</v-chip>
                    </td>
                    <td>
                      <v-btn variant="tonal">Editar</v-btn>
                    </td>
                  </tr>
                  <tr>
                    <td>Zézinho</td>
                    <td>zeo@hotmail.com.br</td>
                    <td>
                      <v-chip variant="outlined" size="small">Convidado</v-chip>
                    </td>
                    <td>
                      <v-btn variant="tonal">Editar</v-btn>
                    </td>
                  </tr>
                </tbody>
          </v-table>
        </v-card>

        <v-row>
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card 
                flat 
                class="border card-hover" 
              >
              <v-img 
                class="align-end text-white"
                src="https://images.pexels.com/photos/19333153/pexels-photo-19333153/free-photo-of-preto-e-branco-p-b-brasil-ponto-de-onibus.jpeg"
              >
                <v-card-title></v-card-title>
              </v-img>

              <v-card-subtitle class="pt-3">Sul do Brasil</v-card-subtitle>
              <v-card-text>
                <div>Top 10 cidades para morar no estado em 2024</div>

                <div>Lorem ipsum dolor sit amet</div>
              </v-card-text>
              <v-card-actions>
                <v-btn variant="outlined" color="primary" >Ver mais</v-btn>
                <v-btn prepend-icon="mdi-cart" variant="tonal" color="warning" >Pacotes</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        
        
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card 
                flat 
                class="border card-hover" 
              >
              <v-img 
                class="align-end text-white"
                src="https://images.pexels.com/photos/1045211/pexels-photo-1045211.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
              >
                <v-card-title></v-card-title>
              </v-img>

              <v-card-subtitle class="pt-3">Curitiba</v-card-subtitle>
              <v-card-text>
                <div>Sta. Felicidade</div>

                <div>Lorem ipsum dolor sit amet</div>
              </v-card-text>
              <v-card-actions>
                <v-btn variant="outlined" color="primary" >Ver mais</v-btn>
                <v-btn prepend-icon="mdi-cart" variant="tonal" color="warning" >Pacotes</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        
        
          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card 
                flat 
                class="border card-hover" 
              >
              <v-img 
                class="align-end text-white"
                src="https://images.pexels.com/photos/12271533/pexels-photo-12271533.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
              >
                <v-card-title></v-card-title>
              </v-img>

              <v-card-subtitle class="pt-3">Curitiba</v-card-subtitle>
              <v-card-text>
                <div>Sta. Felicidade</div>

                <div>Lorem ipsum dolor sit amet</div>
              </v-card-text>
              <v-card-actions>
                <v-btn variant="outlined" color="primary" >Ver mais</v-btn>
                <v-btn prepend-icon="mdi-cart" variant="tonal" color="warning" >Pacotes</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>

          <v-col cols="12" sm="6" md="4" lg="3">
            <v-card 
                flat 
                class="border card-hover" 
                >
              <v-img 
                class="align-end text-white"
                src="https://images.pexels.com/photos/1860705/pexels-photo-1860705.jpeg"
              >
                <v-card-title></v-card-title>
              </v-img>

              <v-card-subtitle class="pt-3">Curitiba</v-card-subtitle>
              <v-card-text>
                <div>Sta. Felicidade</div>

                <div>Lorem ipsum dolor sit amet</div>
              </v-card-text>
              <v-card-actions>
                <v-btn @click="dialog = true" variant="outlined" color="primary" >Ver mais</v-btn>
                <v-btn prepend-icon="mdi-cart" variant="tonal" color="warning" >Pacotes</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>

      
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue';

  const isDrawerOpen = ref(false)
  const isDialogOpen = ref(false)
  const emailRules= [
    value => {
      if(value) {
        return true;
      }
      return 'O email é obrigatório'
    },
    value => {
      if(value.includes('@')) {
        return true;
      }

      return 'Email inválido'
    }
  ];

  const hoveredCard = ref('');

</script>

<style scoped>

  .card-hover:hover {
    background-color: #757575;
  }

</style>