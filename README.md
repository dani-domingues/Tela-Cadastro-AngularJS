# Sobre o Projeto

Este projeto foi desenvolvido como parte de um curso de AngularJS. 
Ele é uma aplicação simples de cadastro de clientes, permitindo listar, adicionar e deletar clientes.  
O objetivo principal é demonstrar como usar AngularJS para construir aplicações dinâmicas com funcionalidades como data binding, filtros, diretivas e controle de eventos.

## O que é AngularJS?
AngularJS é um framework JavaScript de código aberto, mantido pelo Google, que facilita o desenvolvimento de aplicações web dinâmicas.  
Ele segue o padrão MVW (Model-View-Whatever), promovendo a separação de responsabilidades entre dados (Model), interface (View) e lógica de controle (Controller).

## Principais funcionalidades do AngularJS:

- Two-way Data Binding: Atualizações automáticas entre Model e View.
- Dependency Injection: Facilita a injeção de serviços em controladores e diretivas.
- Diretivas Personalizadas: Expande o HTML com novas funcionalidades.
- Filtros: Processa dados antes de exibi-los na interface.
- Testabilidade: Projetado para facilitar o teste de suas aplicações.

## Como usar o projeto

#### Pré-requisitos
- Navegador moderno (Chrome, Firefox, etc.).
- Conhecimento básico de HTML, CSS, JavaScript e AngularJS.
#### Passos para rodar
- Clone este repositório.
- Certifique-se de que os arquivos angular.js, angular-locale_pt-br.js, e bootstrap.min.css estejam no diretório correto.
- Abra o arquivo index.html no navegador.
#### Teste as funcionalidades:
- Adicionar clientes.
- Filtrar a lista de clientes pelo nome.
- Deletar clientes selecionados.

## Estrutura do Projeto

#### 1. Módulo AngularJS

No início do arquivo, definimos o módulo principal `CadastroClientes` e o controlador `CadastroClientesCtrl`:

``` angular.module("CadastroClientes", [])
    .controller("CadastroClientesCtrl", function ($scope) {
        $scope.app = "Cadastro de Clientes"; // Título da aplicação.
        $scope.clientes = [...]; // Lista inicial de clientes.
        ...
    });
```

#### 2. Funcionalidades

**Adicionar Clientes:** Permite adicionar novos clientes à lista:

```
$scope.adicionarClientes = function (cliente) {
    $scope.clientes.push(angular.copy(cliente)); // Adiciona uma cópia do cliente.
    delete $scope.cliente; // Limpa o formulário.
};
```
**Deletar Clientes:** Remove os clientes selecionados:

```$scope.deletarClientes = function (clientes) {
    $scope.clientes = clientes.filter(function (cliente) {
        if (!cliente.selecionado) return cliente;
    });
};
```

**Verificar se há clientes selecionados:** Controla a visibilidade do botão de deletar:

```
$scope.temClienteSelecionado = function (clientes) {
    return clientes.some(function (cliente) {
        return cliente.selecionado;
    });
};
```
#### 3. HTML
O HTML usa diretivas do AngularJS para criar uma interface interativa:

**ng-model:** Liga os dados do formulário ao $scope.  
**ng-repeat:** Itera sobre a lista de clientes.  
**ng-click:** Associa eventos do usuário às funções no controlador.

```
<tr ng-repeat="cliente in clientes | filter: Buscar | orderBy: 'nome'">
    <td><input type="checkbox" ng-model="cliente.selecionado"></td>
    <td>{{cliente.nome | uppercase}}</td>
    <td>{{cliente.codigo}}</td>
    <td>{{cliente.tipoClientes.tipo}}</td>
    <td>{{cliente.data | date: 'dd/MM/yyyy'}}</td>
    <td>{{cliente.valor | currency}}</td>
</tr>
```

## Melhorias Futuras
Adicionar persistência de dados com Local Storage ou API backend.  
Implementar validações mais avançadas nos formulários.  
Substituir AngularJS por um framework mais moderno (Angular, React, ou Vue.js), já que AngularJS está descontinuado.