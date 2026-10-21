# MVP de aplicativo de hidratação

**Usuário:** Cristiano Barichello, Coordenador de TI
**Necessidade:** interface limpa, rápida e sem distrações para registrar água e receber lembretes enquanto trabalha.
**Protótipo interativo:** https://claude.ai/artifact/6F3aEbEiLtNgiCLpUgLn8Q

---

## 1. Escopo (requisitos MUST)

1. Tela inicial com progresso diário da meta de água.
2. Botão único de destaque para registro rápido (+250 ml).
3. Sistema de notificações simulado.

Fora do escopo do MVP: histórico, ajuste de meta, personalização de horários.

---

## 2. Persona e jornada principal

**Perfil de uso:** trabalha em frente a telas, com interrupções constantes (chamados, reuniões). Quer registrar em um toque e voltar ao trabalho, sem animações longas nem textos extensos.

**Jornada (ciclo de ~10 segundos):**

1. **Gatilho:** recebe a notificação "Hora de beber água".
2. **Abertura:** toca na notificação e cai direto na tela principal (ou registra pela própria notificação).
3. **Leitura instantânea:** vê o anel de progresso (ex.: 1.250 de 2.000 ml).
4. **Ação:** toca em **+ 250 ml**.
5. **Feedback:** o anel anima, o número atualiza e aparece uma mensagem curta.
6. **Saída:** fecha o app.

**Princípio de design:** uma tela, uma ação principal, zero fricção.

---

## 3. Wireframe textual: tela principal

```
┌─────────────────────────────┐
│ Boa tarde, Cristiano        │  A. Cabeçalho
│ terça-feira, 20 de outubro  │
│                             │
│        ╭─────────╮          │
│       │  1.250 ml │         │  B. Progresso (elemento herói)
│       │ de 2.000 ml│        │
│       │    62%    │         │
│        ╰─────────╯          │
│                             │
│ 🔔 Próximo lembrete às 15:30│  C. Lembrete (informativo)
│                             │
│ ┌─────────────────────────┐ │
│ │      💧  + 250 ml       │ │  D. Ação principal
│ └─────────────────────────┘ │
│        Desfazer             │
└─────────────────────────────┘
```

### A. Cabeçalho (~10% da altura)
- Saudação com o nome: 18 sp, peso regular.
- Data: 14 sp, cinza com contraste mínimo de 4,5:1.
- Sem menu nem ícones extras.

### B. Progresso diário (~40% da altura), elemento de maior destaque
- Anel circular centralizado, ~70% da largura da tela.
- Trilha em azul claro, preenchimento em azul forte (ex.: `#0A6EBD`), pontas arredondadas.
- Animação suave de 400 ms ao registrar.
- Hierarquia do texto dentro do anel:
  1. Valor atual: 56 sp, negrito.
  2. Meta: 18 sp, regular.
  3. Percentual: 16 sp, semibold.
- O estado nunca depende só da cor: número e percentual sempre visíveis.
- Rótulo para leitor de tela: *"Progresso de hoje: 1.250 de 2.000 mililitros, 62 por cento."*

### C. Status do lembrete (~15% da altura)
- Cartão discreto de uma linha, com sino e horário do próximo lembrete.
- Apenas informativo, não clicável, para não disputar atenção com a ação principal.
- Fundo neutro, texto em 16 sp.

### D. Ação principal (~30% da altura, zona do polegar)
- Botão de largura total (margem lateral de 24 px) e altura mínima de **72 dp**.
- Único elemento colorido e interativo em destaque.
- Texto branco, 24 sp, negrito, contraste acima de 7:1.
- Estados:
  - **Padrão:** azul sólido.
  - **Pressionado:** azul mais escuro e escala em 95%.
  - **Sucesso (1,5 s):** check no botão, vibração curta, anel anima.
  - **Meta atingida:** botão verde com "Meta atingida!", que continua funcional para registros extras.
- **Desfazer:** link discreto de 14 sp, visível por 5 s após cada registro, com área de toque de 48 dp.

### Acessibilidade geral
- Contraste AA no mínimo, AAA no botão principal.
- Áreas de toque de 48 dp ou mais.
- Fonte sem serifa e suporte à ampliação de fonte do sistema.
- Modo escuro automático.
- Respeito à preferência de reduzir movimento.
- Mensagem de feedback anunciada por leitor de tela.

### Princípios aplicados

| Princípio | Aplicação |
|---|---|
| Hierarquia visual | Anel (grande), depois botão (cor forte), depois o resto (neutro) |
| Uma ação principal | Só o botão +250 ml é interativo e colorido |
| Acessibilidade | Contraste, áreas de toque, rótulos e informação nunca só por cor |
| Legibilidade | Fonte sem serifa, mínimo de 14 sp, números em destaque |
| Ergonomia | Botão no terço inferior, alcançável com uma mão |
| Feedback | Animação, vibração e microcopy a cada toque |

---

## 4. Sistema de notificações (simulado)

- Intervalo fixo de 2 horas, das 8h às 20h.
- Notificação local simulada, com botão de ação **Bebi 250 ml** para registrar sem abrir o app.
- Ao registrar (pelo app ou pela notificação), o contador do próximo lembrete reinicia.
- O texto muda conforme o contexto: padrão, atraso e perto da meta.

---

## 5. UI Copy

### Botões e controles

| Elemento | Texto |
|---|---|
| Botão principal | `+ 250 ml` |
| Botão principal (meta batida) | `Meta atingida!` |
| Ação na notificação | `Bebi 250 ml` |
| Desfazer | `Desfazer` |

### Tela principal

| Elemento | Texto |
|---|---|
| Saudação | `Bom dia, Cristiano` / `Boa tarde, Cristiano` |
| Progresso | `1.250 ml` / `de 2.000 ml` / `62%` |
| Próximo lembrete | `Próximo lembrete às 15:30` |
| Estado vazio | `Vamos começar? Toque no botão abaixo.` |

### Feedback após registrar

- `Boa! Mais um copo.`
- `Falta pouco: restam 500 ml.`
- `Meta batida! Parabéns 🎉`

### Notificações

| Momento | Título | Corpo |
|---|---|---|
| Padrão | `Hora de beber água 💧` | `Um gole agora faz diferença.` |
| Sem registro há mais de 3 h | `Sua água está esperando` | `Que tal um copo agora?` |
| Perto da meta | `Quase lá!` | `Faltam só 500 ml.` |

### Leitores de tela

- Botão: `Registrar 250 mililitros de água`
- Anel: `Progresso de hoje: 1.250 de 2.000 mililitros, 62 por cento`

---

## 6. Próximos passos

1. Prototipar no Figma, com os estados do botão e a animação do anel.
2. Testar com 5 usuários e medir se conseguem registrar água em menos de 3 segundos.
3. Depois de validar o MVP, avaliar os requisitos "SHOULD": ajuste de meta, histórico e personalização de horários.
