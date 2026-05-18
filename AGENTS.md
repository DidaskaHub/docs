# Instruções do projeto de documentação

## Sobre este projeto

- Documentação **oficial da Didaska** para usuários da plataforma (donos de escola, administradores, professores e alunos).
- Site construído com [Mintlify](https://mintlify.com). Páginas são arquivos MDX com frontmatter YAML; a configuração fica em `docs.json`.
- `mint dev` roda o preview local; `mint broken-links` valida links internos.

## Público e propósito

- O leitor **não é técnico**. É educador, gestor ou aluno.
- Esta é uma documentação **de produto** (Product Guide): explica o que a plataforma faz e como configurar — não como ela foi construída.

## Limites de conteúdo (obrigatório)

- **Nunca** inclua rotas de API, nomes de tabela, stack, código, nomes internos de feature flags (`addon_*`, `DK-*`), detalhes de banco, infraestrutura ou implementação.
- Não documente o painel interno da equipe Didaska nem ferramentas internas.
- Descreva a navegação pelo que o usuário vê na tela (menus, botões, abas) — nunca por URL/rota.
- Recursos que dependem do plano ou de uma funcionalidade ativada devem ter um aviso (`<Note>`) deixando isso claro, sem citar o identificador técnico.

## Terminologia (use sempre assim)

- A plataforma: **a Didaska** / **a plataforma**.
- Pessoas: **alunos**, **professores**, **administradores**, **proprietário** (não "usuários" genérico quando der para ser específico).
- Áreas: **Cursos**, **Aulas**, **Módulos**, **Simulados**, **Banco de Questões**, **Turmas**, **Lista de Presença**, **Comunidade**, **Didaska AI**, **Monitoria**, **Certificados**, **Site Builder**, **Integrações**, **Aparência**, **Faturamento**, **Funcionalidades**.
- "Sua escola" / "sua plataforma" ao falar com o dono; "seus alunos"; "seu conteúdo".

## Estilo de escrita

- Português do Brasil, **com toda a acentuação correta**.
- Voz ativa e segunda pessoa ("você").
- Frases curtas — uma ideia por frase.
- Títulos em caixa de frase (só a primeira letra maiúscula).
- **Negrito** para elementos da interface: clique em **Configurações**.
- Tom: claro, direto e acolhedor. Confiança sem jargão.

## Componentes Mintlify mais usados

- `<Steps>` / `<Step title="...">` para passo a passo.
- Avisos: `<Note>`, `<Tip>`, `<Warning>`, `<Info>`, `<Check>`.
- `<CardGroup cols={2}>` / `<Card title="..." icon="lucide-icon" href="/rota">`.
- `<Tabs>` / `<Tab title="...">` e `<AccordionGroup>` / `<Accordion title="...">`.
- Ícones: biblioteca **lucide**.
- Links internos sem `.mdx` (ex.: `/cursos/visao-geral`).
- Toda página começa com frontmatter `title` + `description`.
