# ExamplesComponents

Projeto Blazor WebAssembly desenvolvido com **.NET 10** que demonstra na prática os principais recursos de componentização do Blazor.

## 📚 Conceitos Demonstrados

### 1. `@bind` com `EventCallback` (Two-Way Binding)

Localização: `Pages/Counter.razor` e `Pages/Home.razor`

Demonstra o uso de **two-way data binding customizado** entre componentes pai e filho utilizando a convenção `@bind-Propriedade:get` / `@bind-Propriedade:set`.

- O componente `Counter` expõe os parâmetros `Incrementado` e `IncrementadoChanged`
- O componente pai (`Home`) faz o bind usando `@bind-Incrementado:get` e `@bind-Incrementado:set`
- A cada clique no botão, o valor é propagado de volta ao pai via `EventCallback<int>`

```razor
<Counter @bind-Incrementado:get="currentValue"
		 @bind-Incrementado:set="IncrementValue" />
```

---

### 2. `CascadingValue` e `CascadingParameter`

Localização: `Pages/Cascading/LayoutInternoFilho.razor` e `LayoutInternoNeto.razor`

Demonstra como **passar dados para componentes descendentes** sem precisar declarar parâmetros em cada nível da hierarquia.

- O componente raiz (`Home`) envolve a árvore de componentes com `<CascadingValue Value="temaAtual">`
- O componente neto (`LayoutInternoNeto`) acessa o valor com `[CascadingParameter]`
- A comunicação de volta ao pai ocorre via `EventCallback` e `@bind`

```razor
<CascadingValue Value="temaAtual">
	<LayoutInternoFilho />
</CascadingValue>
```

---

### 3. `RenderFragment` com múltiplos slots

Localização: `Pages/RenderFragment/Painel.razor` e `Pages/Home.razor`

Demonstra como criar componentes com **múltiplos slots de conteúdo** usando `RenderFragment`.

- O componente `Painel` possui três slots: `Cabecalho`, `ChildContent` e `Footer`
- O conteúdo de cada slot é definido pelo componente pai na hora do uso
- Permite criar layouts reutilizáveis e altamente flexíveis

```razor
<Painel>
	<Cabecalho><h3>Este é o cabeçalho</h3></Cabecalho>
	<ChildContent><span>Este é o corpo do painel</span></ChildContent>
	<Footer>Este é o footer</Footer>
</Painel>
```

---

## 🗂️ Estrutura do Projeto

```
ExamplesComponents/
├── Pages/
│   ├── Home.razor                        # Página principal que demonstra todos os recursos
│   ├── Counter.razor                     # Componente com two-way binding via EventCallback
│   ├── Cascading/
│   │   ├── LayoutInternoFilho.razor      # Componente filho que recebe EventCallback do neto
│   │   └── LayoutInternoNeto.razor       # Componente neto que lê CascadingParameter
│   └── RenderFragment/
│       └── Painel.razor                  # Componente com múltiplos RenderFragments
├── Layout/
│   ├── MainLayout.razor
│   └── NavMenu.razor
└── wwwroot/
```

## 🚀 Como Executar

```bash
dotnet run --project ExamplesComponents
```

Ou abra a solução no **Visual Studio** e pressione `F5`.

## 🛠️ Tecnologias

- [.NET 10](https://dotnet.microsoft.com/)
- [Blazor WebAssembly](https://learn.microsoft.com/aspnet/core/blazor/)
- [Bootstrap 5](https://getbootstrap.com/)
