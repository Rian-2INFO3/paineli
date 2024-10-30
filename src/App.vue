<template>
 <div class="container">
    <h1>Cardápio do Refeitório IFC</h1>
    
    

    <!-- Filtros para Sem Glúten e Vegetariano -->
    <div class="filters">
      <label>
        <input type="checkbox" v-model="filters.semGluten" />
        Sem Glúten
      </label>
      <label>
        <input type="checkbox" v-model="filters.vegetariano" />
        Vegetariano
      </label>
    </div>

    <!-- Tabela do Cardápio -->
    <table class="menu-table">
      <thead>
        <tr>
          <th>Dia</th>
          <th>Prato Principal</th>
          <th>Acompanhamentos</th>
          <th>Sobremesa</th>
          <th>Sem Glúten</th>
          <th>Vegetariano</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in filteredMenu" :key="index">
          <td>{{ item.dia }}</td>
          <td>{{ item.prato }}</td>
          <td>{{ item.acompanhamentos }}</td>
          <td>{{ item.sobremesa }}</td>
          <td>{{ item.semGluten ? 'Sim' : 'Não' }}</td>
          <td>{{ item.vegetariano ? 'Sim' : 'Não' }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filters: {
        semGluten: false,
        vegetariano: false,
      },
      menu: [
        {
          dia: 'Segunda-feira',
          prato: 'Frango Assado',
          acompanhamentos: 'Arroz, Feijão, Salada',
          sobremesa: 'Fruta',
          semGluten: true,
          vegetariano: false,
        },
        {
          dia: 'Terça-feira',
          prato: 'Macarronada',
          acompanhamentos: 'Batata Frita, Salada',
          sobremesa: 'Pudim',
          semGluten: false,
          vegetariano: true,
        },
        {
          dia: 'Quarta-feira',
          prato: 'Peixe Grelhado',
          acompanhamentos: 'Arroz Integral, Legumes',
          sobremesa: 'Gelatina',
          semGluten: true,
          vegetariano: false,
        },
        {
          dia: 'Quinta-feira',
          prato: 'Carne de Panela',
          acompanhamentos: 'Purê de Batata, Salada',
          sobremesa: 'Sorvete',
          semGluten: true,
          vegetariano: false,
        },
        {
          dia: 'Sexta-feira',
          prato: 'Pizza Vegetariana',
          acompanhamentos: 'Salada Completa',
          sobremesa: 'Bolo',
          semGluten: false,
          vegetariano: true,
        },
      ],
    }
  },
  computed: {
    filteredMenu() {
      return this.menu.filter(item => {
        return (
          (!this.filters.semGluten || item.semGluten) &&
          (!this.filters.vegetariano || item.vegetariano)
        )
      })
    },
  },
}
</script>

<style>
/* * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #f4f4f4;
  min-height: 100vh;
  font-family: Arial, sans-serif;
} */

  

.container {
  width: 100%;
  background-color: #fff;
  padding: 200px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  text-align: center;
}

h1 {
  font-size: 32px;
  margin-bottom: 35px;
  color: #333;
}

.filters {
  margin-bottom: 15px;
  display: flex;
  gap: 10px;
  justify-content: center;
}

.filters label {
  font-size: 16px;
  color: #333;
}

.menu-table {
  width: 100%;
  border-collapse: collapse;
}

.menu-table th,
.menu-table td {
  padding: 12px;
  border: 1px solid #ddd;
}

.menu-table th {
  background-color: #4caf50;
  color: white;
}

@media (max-width: 600px) {
  .menu-table th,
  .menu-table td {
    padding: 8px;
    font-size: 14px;
  }
}
</style>

