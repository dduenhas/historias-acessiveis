# Histórias Acessíveis

**Storytelling sonoro e acessível para a infância**

[![Deploy](https://img.shields.io/badge/demo-Cloudflare%20Pages-f38020?style=for-the-badge&logo=cloudflare&logoColor=white)](https://historias-acessiveis.pages.dev)
[![Licença](https://img.shields.io/badge/licença-MIT-blue?style=for-the-badge)](LICENSE)
[![HTML5](https://img.shields.io/badge/HTML5%20puro-sem%20frameworks-58cc02?style=for-the-badge&logo=html5&logoColor=white)](index.html)
[![BNCC](https://img.shields.io/badge/fundamentação-BNCC-1cb0f6?style=for-the-badge)](index.html)

> Um webapp de narrativas interativas pensado para crianças do Ensino Fundamental I — especialmente estudantes com cegueira total — mediado por professor, familiar ou acompanhante. Tudo funciona no navegador, sem instalação, sem backend e sem dependências externas além da Web Speech API.

---

## Por que este projeto existe?

A literatura infantil costuma chegar às crianças por meio de imagens, tipografia colorida e gestos visuais. Para estudantes com **cegueira total**, esse caminho frequentemente fica bloqueado — não por falta de interesse, mas por falta de **formatos acessíveis e intencionais**.

O **Histórias Acessíveis** responde a essa lacuna com uma proposta simples e poderosa:

- **O som é a linguagem principal** — narração, efeitos sonoros, pausas expressivas e bipes de orientação substituem (ou complementam) o visual.
- **O teclado é o controle** — a criança navega sem mouse, com comandos previsíveis e feedback auditivo imediato.
- **O adulto é o mediador** — o software não substitui o professor ou familiar; ele **potencializa** a mediação pedagógica com dicas, configurações e ritmo ajustável.

A ferramenta dialoga com a **BNCC** nos eixos de oralidade, leitura/escuta ampliada, fruição literária, multissemiose, cultura digital e pensamento computacional — sempre em práticas sociais significativas para os Anos Iniciais do Ensino Fundamental.

---

## Demonstração

Acesse a versão publicada:

**[https://historias-acessiveis.pages.dev](https://historias-acessiveis.pages.dev)**

Ou abra localmente:

```bash
# Opção 1: abrir o arquivo diretamente no navegador
start index.html        # Windows
open index.html         # macOS
xdg-open index.html     # Linux

# Opção 2: servidor local simples
python -m http.server 8765
# Acesse http://localhost:8765
```

> **Recomendação:** use Chrome ou Edge em português (pt-BR) para melhor suporte à síntese de voz.

---

## Como funciona

### Fluxo da experiência

```
┌─────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  Tela       │     │  Modo professor  │     │  História       │
│  inicial    │ ──► │  (configuração)  │ ──► │  (narração +    │
│             │     │                  │     │   escolhas)     │
└─────────────┘     └──────────────────┘     └─────────────────┘
       │                                              │
       └──────── Início direto (história padrão) ──────┘
```

1. **Briefing ao facilitador** — orientações sobre bipes, teclado e mediação.
2. **Escolha de voz** — seta esquerda (feminina) ou direita (masculina), com amostra em tempo real; espaço confirma.
3. **Introdução da história** — contexto narrado antes do primeiro parágrafo.
4. **Narração guiada** — cada trecho é lido em voz alta; ao terminar, um bip (ou a voz do narrador) indica que é hora de pressionar **Espaço**.
5. **Escolhas interativas** — em ramificações, **←** e **→** selecionam opções; **Espaço** confirma.
6. **Revisão** — **↑** e **↓** permitem repetir parágrafos; clique também repete o trecho atual.

### Controles do teclado (modo criança)

| Tecla | Ação |
|-------|------|
| `Espaço` | Avançar / pausar narração / confirmar escolha |
| `↑` `↓` | Navegar entre parágrafos (repetir trechos) |
| `←` `→` | Selecionar opção em momentos de escolha |
| `Home` | Voltar à tela inicial (botão no canto superior esquerdo) |

### Modo professor

O facilitador pode:

- Escolher **faixa etária** (1º–2º ano ou 3º–5º ano)
- Selecionar **tema** entre 6 histórias originais
- Ajustar **velocidade da narração**
- Ativar **texto próprio** — colar um roteiro e conduzir leitura guiada sem ramificações
- Consultar **dicas de mediação pedagógica** durante a história
- Alternar o aviso de continuação entre **bip sonoro** e **voz do narrador**

---

## Histórias incluídas

| Faixa | Título | Tema |
|-------|--------|------|
| 1º–2º ano | **Amigos no Parque** | Animais amigos no parque |
| 1º–2º ano | **Um Dia na Escola** | Rotina na escola |
| 1º–2º ano | **Amigos que se Ajudam** | Amizade e ajuda mútua |
| 3º–5º ano | **Aventura na Cidade Inclusiva** | Cidade e acessibilidade |
| 3º–5º ano | **Viagem ao Espaço** | Exploração e ciência |
| 3º–5º ano | **Respeito e Diversidade** | Convivência e inclusão |

Cada história possui:

- Múltiplas **cenas** com narração em português
- **Ramificações** com escolhas significativas (sem “resposta errada”)
- **Efeitos sonoros** contextuais (mudança de cena, confirmação)
- **Dicas de mediação** para o adulto — perguntas, objetos concretos, estratégias de reconto

---

## Acessibilidade

O projeto foi construído com critérios explícitos de acessibilidade:

- **Skip link** para pular ao conteúdo principal
- **Regiões ARIA** com `aria-live` para atualizações dinâmicas
- **Foco visível** em todos os elementos interativos (WCAG 2.4.7)
- **Classe `.sr-only`** para textos exclusivos de leitores de tela
- **`prefers-reduced-motion`** respeitado no CSS
- **Sem dependência de mouse** no modo criança
- **Contraste e tipografia** legíveis (Nunito + serifada para o texto da história)
- **Grifo visual** amarelo na narrativa e azul claro nas orientações (apoio para baixa visão residual ou co-mediação visual)

---

## Arquitetura técnica

Aplicação **single-file** em HTML, CSS e JavaScript puro — sem React, sem bundler, sem servidor.

```
historias-acessiveis/
├── index.html          # Aplicação completa (entrada principal)
├── storytelling.html   # Cópia equivalente (compatibilidade)
├── README.md
└── .gitignore
```

### Módulos JavaScript

| Módulo | Responsabilidade |
|--------|------------------|
| `AudioManager` | Síntese de voz (Web Speech API), efeitos sonoros, pausa/retomada |
| `KeyboardManager` | Roteamento centralizado de eventos de teclado por tela/modo |
| `StoryStateMachine` | Estados: briefing, seleção de voz, intro, narração, pausa, escolhas, revisão |
| `StoryManager` | Catálogo `STORIES`, filtros por idade/tema, texto personalizado |
| `TextDisplay` | Exibição sincronizada de narrativa, orientações e destaques |
| `TeacherUI` | Formulário de configuração e validação |
| `TeacherStoryControls` | Painel lateral durante a história (velocidade, bip/voz, dicas) |
| `PedagogyModal` | Fundamentação pedagógica alinhada à BNCC |
| `App` | Bootstrap, troca de telas, foco inicial, fluxo global |

### Como adicionar uma nova história

1. Copie um objeto existente no array `STORIES` em `index.html`.
2. Altere `id`, `title`, `ageGroup` (`'1-2'` ou `'3-5'`), `theme` e `themeLabel`.
3. Escreva as cenas em `scenes` — cada cena precisa de `id` e `narration`.
4. Para ramificações, adicione `choice` com `options` e `nextSceneId`.
5. Em cenas lineares, use `nextSceneId` ou deixe a ordem do array definir o fluxo.
6. Inclua `mediationTips` com 3–5 orientações para o facilitador.

---

## Fundamentação pedagógica

O botão **coruja** (canto superior direito) abre um modal com a fundamentação completa do webapp, articulando:

- Finalidade educacional do software
- Convergência com a BNCC (Língua Portuguesa, Arte, Computação)
- Tabela de habilidades convergentes (EF15LP09, EF15LP10, EF15LP15, etc.)
- Contribuições específicas: oralidade, fruição literária, multissemiose, cultura digital
- Papel do professor ou acompanhante na mediação

---

## Público-alvo

| Perfil | Uso |
|--------|-----|
| **Crianças com cegueira total** | Escuta ativa, escolhas por teclado, participação oral mediada |
| **Professores de Educação Especial / inclusiva** | Seleção de histórias, dicas de mediação, texto próprio |
| **Familiares e cuidadores** | Contação de histórias acessível em casa |
| **Pesquisadores em acessibilidade digital** | Referência de design centrado no canal auditivo |

---

## Requisitos

- Navegador moderno com suporte a **Web Speech API** (`speechSynthesis`)
- **JavaScript** habilitado
- Voz em **português brasileiro** instalada no sistema operacional
- **Fones de ouvido** recomendados em ambientes coletivos

---

## Deploy

O projeto está hospedado na **Cloudflare Pages** com deploy direto do repositório GitHub.

```bash
# Deploy manual (requer Wrangler autenticado)
npx wrangler pages deploy . --project-name=historias-acessiveis --branch=main
```

---

## Contribuindo

Contribuições são bem-vindas — especialmente:

- Novas histórias com ramificações acessíveis
- Melhorias na síntese de voz e fallbacks para navegadores
- Traduções e adaptações regionais
- Relatos de uso em sala de aula

1. Faça um fork do repositório
2. Crie uma branch (`git checkout -b feature/minha-melhoria`)
3. Commit suas alterações
4. Abra um Pull Request

---

## Licença

Este projeto é distribuído sob a licença **MIT**. Veja o arquivo [LICENSE](LICENSE) para detalhes.

---

## Autor

Desenvolvido por [dduenhas](https://github.com/dduenhas) como ferramenta de storytelling acessível para a educação inclusiva.

---

<p align="center">
  <strong>Histórias Acessíveis</strong> — porque toda criança merece ouvir, imaginar e escolher seu caminho na narrativa.
</p>
