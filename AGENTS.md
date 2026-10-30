# Documentação pública da Didaska

Este repositório é a **única documentação pública da Didaska**, publicada em
[docs.didaska.com.br](https://docs.didaska.com.br) pelo Mintlify a partir da
branch `main`.

## Fluxo de trabalho

- Todo trabalho nasce de uma issue **DK-XXXX** no Linear. A branch tem o nome da
  issue (`DK-XXXX`) e o título e a descrição do PR a referenciam.
- PR sempre para `develop`. Nunca abra PR direto para `main`.
- `develop → main` **publica em produção**. Esse PR acompanha a release do
  produto: a documentação de um recurso só vai para `main` quando o recurso está
  em produção.
- Nada de push em `main` nem force push.

Site de documentação para **quem usa** a plataforma — administradores,
professores e alunos das instituições. Construído em [Mintlify](https://mintlify.com).

Isto **não** é documentação interna. Decisão de arquitetura, convenção de código
e o que um módulo faz por dentro moram nos repositórios do produto. Aqui só
entra o que o cliente precisa saber para usar o produto.

O leitor **não é técnico**: é educador, gestor ou aluno. Esta é uma documentação
de produto — explica o que a plataforma faz e como configurar, não como ela foi
construída.

## Como mexer

```bash
bun install
bun run dev            # sobe em http://localhost:3000
bun run broken-links   # procura link quebrado
```

O `package.json` só fixa a versão do `mint`. O Mintlify ignora `node_modules/`
na publicação.

Página é MDX com frontmatter YAML. A navegação vive em `docs.json` — **página
que não está no `docs.json` não aparece no site**, e página listada que não
existe quebra o build.

## Regra de atualização

**Mudança de comportamento visível ao usuário atualiza a documentação no mesmo
PR.** Vale para: recurso novo, fluxo alterado, campo renomeado, limite mudado,
recurso removido.

Se a mudança não é visível ao usuário, não escreva nada aqui. Documentação
inflada com detalhe interno é tão ruim quanto documentação desatualizada — e as
duas fazem as pessoas pararem de ler.

## Um produto só

A Didaska é só a edição hospedada (a antiga separação SaaS/PaaS acabou em
29/10/2026). O site tem uma aba, o **Guia do produto**. O grupo **Sua
plataforma** (pasta `saas/`) reúne assinatura, endereço, domínio próprio,
planos, limites, suporte e exclusão; o resto mora nos grupos de cada área.

Não escreva "Didaska SaaS", "Didaska PaaS", "edição" nem "instalação
própria". Os endereços antigos (`/paas/*`, `/produto/edicoes`) têm
redirecionamento em `docs.json`.

## Como escrever

- **Segunda pessoa e voz ativa.** "Você cria o curso", não "o curso é criado".
- **Uma ideia por frase.** Frase longa em documentação é releitura.
- **Título em caixa de sentença.** "Criar um curso", não "Criar Um Curso".
- **Negrito para elemento de interface:** clique em **Configurações**.
- **Código para nome de arquivo, comando e caminho:** `docker compose up -d`.
- **Diga o que acontece depois.** Toda página termina apontando o próximo passo
  ou o assunto vizinho.
- **Nunca prometa o que o produto não faz.** Documentação é contrato.

Escreva em **português do Brasil**, do jeito que a interface fala. Se a tela diz
"Usuários", a documentação diz Usuários — não "membros", não "pessoas".

## Vocabulário

Use o termo que a interface usa. Quando houver conflito, a interface ganha e a
documentação é corrigida.

| Use | Não use |
|---|---|
| plataforma | tenant, workspace, instância |
| curso, módulo, aula | trilha, capítulo, lição |
| prova | simulado, exame, avaliação (quando for a prova formal) |
| turma | classe, grupo, cohort |
| matrícula | inscrição, enrollment |

Termo do produto em português. Nada de vocabulário de engenharia vazando para
cá: o cliente não sabe o que é tenant, outbox ou fila.

## Limites do conteúdo

Não documente:

- detalhe de implementação, arquitetura ou stack;
- rota interna, nome de tabela, nome de serviço;
- recurso ainda não lançado — inclusive "em breve";
- endereço interno, valor de configuração de produção, nome de servidor;
- nome interno de feature flag ou de issue (`addon_*`, `DK-*`);
- painel interno da equipe Didaska ou ferramenta interna;
- passo que só a equipe da Didaska executa.

Documente:

- o que o cliente vê, faz e configura;
- o que acontece quando algo dá errado, e o que ele pode fazer;
- limite, prazo e regra que afetam a decisão dele;

## Detalhes de escrita

- Português do Brasil **com toda a acentuação correta**.
- Tom claro, direto e acolhedor. Confiança sem jargão.
- Descreva a navegação pelo que a pessoa vê na tela (menus, botões, abas) —
  nunca por URL ou rota.
- Recurso que depende do plano ou de uma funcionalidade ativada leva um aviso
  (`<Note>`) deixando isso claro, sem citar o identificador técnico.
- Toda página começa com frontmatter `title` + `description`.
- Links internos sem `.mdx` (ex.: `/produto/cursos/criar-curso`).

## Componentes Mintlify mais usados

- `<Steps>` / `<Step title="...">` para passo a passo.
- Avisos: `<Note>`, `<Tip>`, `<Warning>`, `<Info>`, `<Check>`.
- `<CardGroup cols={2}>` / `<Card title="..." icon="lucide-icon" href="/rota">`.
- `<Tabs>` / `<Tab title="...">` e `<AccordionGroup>` / `<Accordion title="...">`.
- Ícones: biblioteca **lucide**. Nunca emoji.

## Identidade visual

Tema, cores, logo (`logo/`), favicon e rodapé ficam em `docs.json` e
`style.css`. Mudança de navegação mexe só em `navigation`; o resto é
identidade e não muda junto com conteúdo.

## Screenshot

Imagem envelhece mais rápido que texto e é o que mais desatualiza um site de
documentação. Use só quando a tela é realmente difícil de descrever.

Quando usar: sem dado real, sem nome de pessoa, sem e-mail. Versão clara e
escura quando o contraste importar.

## Antes de abrir PR

```bash
bun run broken-links
```

E leia a página no navegador. Erro de MDX aparece renderizado, não no lint.
