# MVP de Aplicativo de Hidratação

**Usuário:** Cristiano Barichello, Coordenador de TI  
**Necessidade:** Interface limpa, rápida e sem distrações para registrar água e receber lembretes enquanto trabalha, contendo onboarding inicial para cadastro de nome e definição de meta personalizada.  
**Protótipo Interativo:** https://claude.ai/artifact/6F3aEbEiLtNgiCLpUgLn8Q

---

## 1. Escopo (Requisitos MUST)

1. **Tela de Onboarding / Configuração Inicial:** Cadastro do nome do usuário e definição da meta diária de água através de uma barra de rolagem (*slider*).
2. **Tela Principal com Progresso Diário:** Exibição dinâmica da meta definida e do progresso atual.
3. **Botão Único de Destaque:** Registro rápido de consumo (`+ 250 ml`).
4. **Sistema de Notificações Simulado.**
5. **Histórico Diário:** Registro e visualização dos consumos efetuados ao longo do dia.

---

## 2. Paleta de Cores (Tons de Azul Escuro)

Para garantir uma interface sóbria, elegante e sem fadiga visual (ideal para longas jornadas em frente a telas de computadores em ambientes corporativos de TI), a identidade visual adota uma paleta focada em **tons de azul escuro**:

| Cor | Hexadecimal | Aplicação na Interface |
|---|---|---|
| **Azul Meia-Noite (Fundo Principal)** | `#0B132B` | Fundo geral da aplicação no modo escuro |
| **Azul Profundo (Superfícies / Cartões)** | `#1C2541` | Cards, blocos de informações e fundo do anel |
| **Azul Tecnológico (Bordas / Suporte)** | `#3A506B` | Bordas secundárias, linhas e elementos desativados |
| **Azul Elétrico / Ciano (Destaque e Progresso)** | `#48CAE4` | Anel de progresso ativo, botão principal e ícones |
| **Branco / Gelo (Textos e Elementos)** | `#E0FBFC` / `#FFFFFF` | Textos principais, títulos e rótulos de alta legibilidade |

---

## 3. Persona e Jornada Principal

**Perfil de Uso:** Trabalha focado em frente a telas, com interrupções constantes (chamados, reuniões, servidores). Quer registrar em um toque e voltar ao trabalho, sem animações longas ou telas poluídas.

**Jornada do Usuário:**

1. **Onboarding (Primeiro Acesso):**
   - Insere o nome: **Cristiano Barichello**.
   - Ajusta a meta diária usando a barra de rolagem (ex.: **2.500 ml**).
   - Confirma em **"Começar"**.
2. **Uso Diário (~10 segundos):**
   - **Gatilho:** Recebe a notificação *"Hora de beber água 💧"*.
   - **Abertura:** Toca na notificação e cai direto na tela principal.
   - **Leitura Instantânea:** Vê o anel de progresso (ex.: **1.250 de 2.500 ml** / **50%**).
   - **Ação:** Toca no botão principal **+ 250 ml**.
   - **Feedback:** O anel anima, o número atualiza e o histórico registra a entrada com o horário.
   - **Saída:** Retorna imediatamente às atividades de trabalho.

---

## 4. Wireframe Textual: Tela de Onboarding (Novo)

```
┌─────────────────────────────┐
│ Configuração Inicial        │  A. Título
│                             │
│ Como podemos te chamar?     │
│ ┌─────────────────────────┐ │
│ │ Cristiano Barichello    │ │  B. Campo de Nome
│ └─────────────────────────┘ │
│                             │
│ Qual é a sua meta diária?   │
│ [========O============== ] │  C. Barra de Rolagem (Slider)
│        2.500 ml             │     1.000 ml a 5.000 ml
│                             │
│ * Recomendado: 2.000 ml     │
│                             │
│ ┌─────────────────────────┐ │
│ │        Começar          │ │  D. Botão Avançar (#48CAE4)
│ └─────────────────────────┘ │
└─────────────────────────────┘
```

### A. Título e Instrução
- Texto em 20 sp, peso semibold, cor `#E0FBFC`.

### B. Campo de Nome
- Input de texto para inserção/confirmação do nome (`Cristiano Barichello`).
- Fundo `#1C2541`, borda `#3A506B`, texto branco `#FFFFFF`.

### C. Barra de Rolagem (Slider) para Meta de Água
- Permite arrastar fluidamente de **1.000 ml** até **5.000 ml** (incrementos de 250 ml).
- Exibe o valor selecionado em destaque tipográfico (28 sp, negrito, cor `#48CAE4`) logo abaixo da barra.
- Ajusta a meta do anel de progresso na tela principal automaticamente.

### D. Botão Avançar
- Largura total, altura de 56 dp, cor de fundo `#48CAE4` com texto escuro `#0B132B`.
- Direciona o usuário para a tela principal.

---

## 5. Wireframe Textual: Tela Principal (Atualizada)

```
┌─────────────────────────────┐
│ Boa tarde, Cristiano        │  A. Cabeçalho (Nome cadastrado)
│ terça-feira, 20 de outubro  │
│                             │
│        ╭─────────╮          │
│       │  1.250 ml │         │  B. Progresso diário
│       │ de 2.500 ml│        │     (Baseado no slider: 50%)
│       │    50%    │         │
│        ╰─────────╯          │
│                             │
│ 🔔 Próximo lembrete às 15:30│  C. Status do lembrete
│                             │
│ ┌─────────────────────────┐ │
│ │      💧  + 250 ml       │ │  D. Ação principal (#48CAE4)
│ └─────────────────────────┘ │
│        Desfazer             │
└─────────────────────────────┘
```

### A. Cabeçalho (~10% da altura)
- Saudação dinâmica com o nome cadastrado no onboarding: *“Boa tarde, Cristiano”*.
- Data atual: 14 sp, cor `#E0FBFC` com transparência.

### B. Progresso Diário (~40% da altura)
- Anel circular centralizado (largura ~70% da tela).
- Trilha em azul escuro profundo (`#1C2541`), preenchimento em azul elétrico (`#48CAE4`).
- Valores internos:
  1. Consumo atual: 56 sp, negrito (`#FFFFFF`).
  2. Meta definida: 18 sp (`#E0FBFC`).
  3. Percentual: 16 sp, semibold (`#48CAE4`).

### C. Status do Lembrete (~15% da altura)
- Cartão com ícone de sino e horário do próximo alerta.
- Fundo `#1C2541`, texto em 16 sp.

### D. Ação Principal (~30% da altura, zona do polegar)
- Botão de largura total (altura mínima: **72 dp**).
- Cor de fundo `#48CAE4`, texto em tom escuro contrastante (`#0B132B`), 24 sp, negrito.
- Link **Desfazer** visível por 5 segundos após a inserção.

---

## 6. Sistema de Notificações (Simulado)

- Intervalos configuráveis de 2 horas (das 08:00 às 20:00).
- Ação rápida na notificação: **"Bebi 250 ml"** (registra sem necessidade de abrir a interface).
- Ao registrar, calcula dinamicamente o próximo horário de lembrete.

---

## 7. UI Copy

### Onboarding e Configuração Initial
| Elemento | Texto |
|---|---|
| Título da Tela | `Configuração Inicial` |
| Rótulo do Nome | `Como podemos te chamar?` |
| Rótulo da Meta | `Qual é a sua meta diária de água?` |
| Botão de Confirmação | `Começar` |

### Tela Principal
| Elemento | Texto |
|---|---|
| Saudação | `Bom dia, Cristiano` / `Boa tarde, Cristiano` |
| Progresso | `1.250 ml` / `de 2.500 ml` / `50%` |
| Botão Principal | `+ 250 ml` |
| Botão (Meta Batida) | `Meta atingida!` |
| Desfazer | `Desfazer` |
| Lembrete | `Próximo lembrete às 15:30` |

### Microcopy de Feedback
- `Boa! Mais um copo. 💧`
- `Falta pouco: restam 500 ml.`
- `Meta batida! Parabéns 🎉`

---

## 8. Implementação do Histórico Diário

- **Armazenamento:** Persistência em `localStorage` sob a chave `bebaAguaHistory`.
- **Estrutura de Dados:** Registros indexados por data `YYYY-MM-DD` contendo quantidade (`amount`) e carimbo de data/hora (`timestamp`).
- **Comportamento Visível:**
  - Card dedicado com o título **"Consumo de hoje"**.
  - Lista em ordem cronológica inversa (mais recente no topo).
  - Resumo comparativo dos últimos 7 dias em barras horizontais.
  - Opção de desfazer/remover o último registro.

---

## 9. Próximos Passos

1. Exportar e testar os fluxos no protótipo visual (onboarding + slider + tela principal + histórico).
2. Validar o nível de contraste (Acessibilidade WCAG AA/AAA) nos tons de azul escuro `#0B132B` e `#48CAE4`.
3. Concluir a entrega com a nomenclatura padrão: `Cristiano_Barichello_Aula1_AppBeberAgua`.