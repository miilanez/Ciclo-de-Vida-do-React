# Desenvolvimento para Web com React sem Create React App

Uma das coisas mais interessantes que vi durante o estudo de Desenvolvimento para Web com React, é aprender como funciona o React SEM instalar o CRA (Create React App) ou derivados (Next, Vite, etc.). É o React sendo usado dentro de um arquivo HTML simples usando CDN.

## A história do React

O React foi uma solução encontrada em meados de 2011 pelos engenheiros de software do Facebook para solucionar dificuldades no processo de manutenção do código da rede. O Facebook estava em um período de grande expansão e com muitos novos usuários migrando para o mesmo.

A plataforma foi adicionando cada vez mais funcionalidades, membros na equipe de desenvolvimento e mais complexidade, até que não era mais possível acompanhar o ritmo das atualizações e consequentemente, uma melhoria para se tornar mais escalável e eficiente.

ReactJS começou através do XHP, uma versão do PHP que o Facebook lançou em 2010. XHP foi principalmente desenvolvido para minimizar os ataques de Cross Site Scripting (XSS), que é uma vulnerabilidade do sistema quando uma pessoa tenta inserir códigos nas páginas web. Mas aplicações web dinâmicas geralmente precisam de muitas requisições, e XHP não conseguia lidar com essa parte.

Até que, um engenheiro do Facebook (Jordan Walke) negociou com o seu gestor para levar XHP para o browser usando JavaScript e entraram em acordo para experimentar por 6 meses. O resultado desse experimento é o nascimento do ReactJS.

# Ciclo de Vida do Componente React

## Fase de Inicialização
- Configura as props e o estado inicial do componente (conferir linhas 20 a 27).

## Fase de Montagem

1. **constructor(props):**
   - Primeiro método chamado.
   - Usado para inicializar o estado (`state`) e fazer o bind de métodos.
   - No código, inicializa o estado com `nome: "Gabriel"`.

2. **static getDerivedStateFromProps(props, state):**
   - Chamado antes de `render`, tanto na montagem quanto nas atualizações.
   - Usado para atualizar o estado baseado nas props.
   - No código, retorna `null` (não modifica o estado).

3. **componentWillMount():** [Depreciado]
   - Este método está em desuso desde o React 16.3 e **não é mais recomendado** seu uso.

4. **render():**
   - Método obrigatório.
   - Retorna o JSX que será renderizado.
   - No código, renderiza um título com o nome e cor, um botão e um input.

5. **componentDidMount():**
   - Chamado após o componente ser montado no DOM.
   - Ideal para requisições HTTP, subscrições ou manipulações do DOM.

## Fase de Atualização

1. **static getDerivedStateFromProps(props, state):**
   - Chamado novamente antes de cada atualização.

2. **shouldComponentUpdate():**
   - Decide se o componente deve ser re-renderizado.
   - No código, sempre retorna `true`.

3. **render():**
   - Chamado novamente para re-renderizar o componente.

4. **getSnapshotBeforeUpdate(prevProps, prevState):**
   - Chamado antes das mudanças serem aplicadas ao DOM.
   - Pode capturar informações do DOM antes da atualização.

5. **componentDidUpdate():**
   - Chamado após a atualização ser aplicada.
   - Bom para operações após uma atualização.

### No código, as atualizações podem ocorrer de três formas:
- Clicando no botão "Mudar nome" que chama `changeName()`.
- Digitando no input, que atualiza o estado através do `onChange`.
- Quando as props mudam (embora isso não aconteça no exemplo).

## Fluxo de Execução

### Fluxo de Inicialização
1. Definição de `defaultProps`
2. Definição do estado inicial

### Fluxo de Montagem
1. `constructor`
2. `getDerivedStateFromProps`
3. `componentWillMount` (em desuso)
4. `render`
5. `componentDidMount`

### Fluxo de Atualização do Estado (exemplo: ao clicar no botão)
1. `getDerivedStateFromProps`
2. `shouldComponentUpdate`
3. `render`
4. `getSnapshotBeforeUpdate`
5. `componentDidUpdate`

### Fluxo de Desmontagem
1. `componentWillUnmount`


## Algumas observações importantes:

- O método `componentWillMount` está em desuso e não deve ser usado em novos projetos, aqui ele serve apenas para explicação;
- Como falei no início, esse formato é apenas para fim acadêmico e é uma boa prática usar componentes funcionais com Hooks em projetos modernos.

