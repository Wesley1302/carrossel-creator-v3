# REF_09: GATES DE VALIDAÇÃO + REGRAS DE LEGIBILIDADE

Uso interno — nunca mencionar gates ao usuário. Cada gate é bloqueio: sem validação, sem avanço.
Este arquivo é a **fonte canônica** de: área segura, contraste, contador, hierarquia e legibilidade. Outros arquivos referenciam daqui.

---

## PARTE 1 — REGRAS DE LEGIBILIDADE (canônicas)

**Regra sagrada:** o texto é sempre o elemento principal do card. Visual serve à mensagem. Se o leitor precisa de esforço para ler, o card falhou. Legibilidade > estética, sempre.

### Hierarquia do card (ordem de prioridade)
1. Head/Hook ou elemento visual principal → 2. Body/mensagem principal → 3. CTA/instrução → 4. Contador (discreto) → 5. Elementos de apoio → 6. Decoração.
Contador, apoio e decoração nunca competem com 1-3. No Card 1, o hook é o primeiro elemento percebido.

### Área segura
- Mínimo **80px** de todas as bordas para texto crítico (hook, body, CTA, contador, texto em elemento gráfico).
- Decorativos podem sangrar até a borda; em infinito, podem atravessar cortes — texto crítico nunca.
- Mobile first: em telas pequenas a área percebida encolhe; margem com folga.

### Contraste
- Piso: **4.5:1 (WCAG AA)**.
- Branco → sobre área escura (overlay 50-70%, escurecimento, gradiente controlado). Preto → sobre área clara/sólida. Evitar cinza sobre cinza, textura forte atrás de texto, foto complexa como fundo direto.

### Texto sobre imagem
Nunca sobre rosto, olhos, produto principal ou textura detalhada. Técnicas válidas (usar UMA): overlay 50-70% · blur · escurecimento/clareamento · gradiente · caixa sutil · espaço negativo. Decisão rápida: imagem essencial → mover o texto; texto essencial → escurecer a imagem.

### Texto sobre elementos gráficos
Shapes/ícones/linhas não atravessam texto · padrões de fundo com 30-50% de opacidade · gráficos/tabelas só se legíveis no mobile.

### Tipografia
Máx 2 famílias por card · display com peso/tamanho claramente maior que body · body em sans-serif simples · sem ALL CAPS em blocos longos · sem texto fino sobre fundo escuro · negrito/cor com moderação. Exceção: lettering do elemento visual pode ser expressivo, desde que legível.

### Tamanho (proporção, não pixels rígidos)
Hook = primeiro elemento percebido · body legível em tela de ~6" · contador pequeno mas legível · CTA claro. Teste: "precisa de zoom? aumenta."

### Contador de slides (regra canônica)
- **Card 1: sem contador. Nunca "1/N". Sem exceção — nem em exemplos.**
- Cards 2+: "[N]/[TOTAL]" discreto · canto superior ou inferior direito (consistente) · opacidade 40-70% · cor secundária/neutra · pill/caixa só se a referência aprovada usar · nunca compete com texto · em infinito: cada zona tem o seu, nunca cruza corte.

### Legibilidade por função narrativa
Hook: impacto com leitura instantânea · Setup: respiro · Build: hierarquia de progressão · Interest Peak: a informação central é a mais fácil de ler do carrossel · Climax: contraste alto, texto sempre legível · Payoff: clareza de resolução · CTA: layout limpo, energia baixa/focada, ação evidente.

### Por caminho visual
**A (fotográfico):** texto em zona limpa com negative space · overlay/gradiente quando preciso · luz conduz o olhar ao texto.
**B (tipográfico):** zero linguagem de câmera · grid claro · formas apoiam a leitura · consistência entre cards.
**C (infinito):** texto crítico na área segura de cada zona · nada crítico sobre linha de corte · cada card funciona sozinho · sem divisórias visíveis.

### Matriz fundo → ação
| Fundo | Fazer |
|---|---|
| Foto clara | overlay escuro, gradiente ou mover texto |
| Foto escura | texto claro com contraste validado |
| Cor vibrante | texto neutro, área limpa |
| Textura forte | reduzir opacidade ou blur |
| Ilustração detalhada | caixa, espaço negativo ou reposicionar |
| Gradiente | validar contraste no ponto exato do texto |

### Checklist rápido de legibilidade
- [ ] Hook é o primeiro elemento percebido? Body legível em ~6"?
- [ ] Contraste ≥4.5:1? Texto na área segura? Nada cobre texto?
- [ ] Fundo controlado? Elementos apoiam (não competem)? Contador discreto? CTA claro?
- [ ] Cada card funciona sozinho? Infinito sem texto cruzando corte? Zoom desnecessário?

Frases operacionais (usar com o usuário quando detectar problema): copy longa → "Esse texto pode pesar visualmente. Ajustamos a copy ou resolvo com hierarquia e quebra de linha?" · fundo competindo → "Vou preservar o estilo e criar uma área mais limpa para o texto." · infinito com risco → "O texto precisa ficar dentro de cada zona de corte. Vou reposicionar."

---

## PARTE 2 — GATES DO CARROSSEL

### GATE 0 — COLETA
- [ ] Nicho, tema e objetivo informados · conteúdo pronto ou construir junto definido · temperatura considerada · idioma definido · automação perguntada (uma vez) · estado de sessão iniciado
**Bloqueio:** sem nicho + tema + objetivo, perguntar antes de continuar.

### GATE 1 — ESTRATÉGIA
- [ ] 1 objetivo · 1 promessa · estrutura escolhida e justificada · hook do banco (número e nome, REF_01) · CTA alinhado (REF_03) · temperatura considerada · zero dados inventados · promessa cabe no payoff · quantidade 5-10 sugerida com justificativa
**Bloqueio:** erro em estrutura/hook/CTA → corrigir. Próximo passo: gate de quantidade explícito.

### GATE 2 — QUANTIDADE
- [ ] Usuário CONFIRMOU (ou delegou explicitamente) · 5-10 · sem padding nem compressão
**Bloqueio:** sem confirmação, não escrever copy.

### GATE 3 — COPY
- [ ] Exatamente N cards · Card 1 = hook sem body · Card 2 re-hooka · progressão Setup→Build→Peak/Climax · payoff após tensão, antes do CTA · Card N = 1 CTA único
- [ ] 1 ideia/card · headlines ≤6 palavras quando usadas · body ≤3 linhas · 30-40 palavras (60 justificado) · linguagem clara e humana
- [ ] Zero números/provas/ofertas inventados · placeholders onde falta dado · zero estatística das referências internas reproduzida como fato · contexto do usuário mantido
- [ ] Recompensa do deslize validada card a card
**Bloqueio:** qualquer falha → corrigir antes de apresentar.

### GATE 4 — CTA (específico)
- [ ] Alinhado ao objetivo · intensidade compatível com temperatura · sem urgência falsa · automação verificada (palavra-gatilho real, 1 palavra) · freebie específico · seguir com promessa concreta · comentar com pergunta binária/curta · sem CTAs concorrentes
**Bloqueio:** CTA fraco/desalinhado → reescrever.

### GATE 5 — DIREÇÃO VISUAL
- [ ] Referência solicitada/analisada ou criação do zero justificada · copy NÃO alterada · sistema consistente · energia por função conforme matriz (REF_06) — sem exceções · texto sempre elemento principal · nenhuma proibição absoluta violada (checar card a card, inclusive nas próprias sugestões) · Distinctive Audit rodado · usuário APROVOU · zero cópia de propriedade protegida
**Bloqueio:** legibilidade, competição ou proibição violada → ajustar.

### GATE 6 — LEGIBILIDADE (crítico — paralisa até resolver)
- [ ] Checklist rápido da Parte 1 inteiro OK
**Bloqueio:** falhou → paralisa; ajustar visual ou propor ajuste de copy.

### GATE 7 — CONTADOR
- [ ] Card 1 sem · Cards 2+ com, discreto, posição consistente, 40-70% opacidade · em infinito: por zona, sem cruzar corte · pill só se aprovado
**Bloqueio:** contador no Card 1 ou chamativo → corrigir antes dos prompts.

### GATE 8 — CAMINHO VISUAL
- [ ] A: câmera/luz coerentes · **A-Realista: camada de realismo aplicada, SEM 85mm/studio/commercial** · text zone protegida
- [ ] B: zero linguagem de câmera · grid e hierarquia definidos · cores com função
- [ ] C: 2-3 cards consecutivos definidos · motivo narrativo · canvas 2160x1350/3240x1350 (fallback declarado como aproximação) · zero divisórias · texto 80px por zona · cada card funciona só
**Bloqueio:** caminho errado → corrigir antes de gerar.

### GATE 9 — PROMPTS FINAIS
- [ ] JSON válido por card (schema REF_07) · em inglês · copy preservada em `exact_visible_text` (zero tradução/reescrita/adaptação) · proporção correta · contador correto · sistema travado consistente · `quality.avoid` cobre proibições · zero dado inventado · zero propriedade protegida · prompts específicos (nunca genéricos)
**Bloqueio:** qualquer falha → reescrever antes de entregar.

### GATE 10 — LEGENDA (Etapa G)
- [ ] Linha 1 re-ganchea sem repetir o hook literal · corpo agrega (não resume cards) · CTA espelha o do último card (palavra-gatilho se automação=sim) · 3-5 hashtags de nicho · alt text por card · zero dado inventado · zero segundo CTA
**Bloqueio:** legenda com CTA divergente do card final → alinhar.

---

## PARTE 3 — GATES DO REELS

### GATE 0-R — COLETA
- [ ] Nicho/persona · objetivo · tema · tom · dados reais (quais?) · automação · formato desejado
**Bloqueio:** sem objetivo + tema + tom, não iniciar.

### GATE 1-R — HOOK
- [ ] 2-3 opções com tipo (número e nome, REF_01) · dado real ou placeholder · Jeff Nippard com número concreto + contraintuição (e estudo real) · aprovação explícita
**Bloqueio:** sem aprovação, não desenvolver roteiro.

### GATE 2-R — ROTEIRO
- [ ] Hook 0-3s específico · 150-250 palavras · payoff presente · 1 CTA alinhado + automação · cada bloco entrega algo novo · ritmo varia · zero dado inventado · aprovação explícita
**Bloqueio:** sem aprovação, não gerar direções.

### GATE 3-R — DIREÇÕES
- [ ] Nativa: elemento definido, instrução clara, timing, não encenado, não compete com a fala
- [ ] Gráfica: máx 2-3 elementos, timing preciso, coerente com identidade, complementa
- [ ] Entrega completa nas 3 camadas, na ordem roteiro → nativa → gráfica
**Bloqueio:** camada faltando → completar.

---

## MATRIZ RÁPIDA DE BLOQUEIO

| Erro | Ação | Avança? |
|---|---|---|
| Copy não aprovada | aguardar aprovação | ❌ |
| Quantidade não confirmada | perguntar de novo | ❌ |
| Texto ilegível | ajustar visual ou copy | ❌ |
| CTA desalinhado | corrigir antes de aprovar | ❌ |
| Dados inventados | placeholder ou pedir dado real | ❌ |
| Estatística interna citada como fato | reformular como heurística ou remover | ❌ |
| Referência com logo protegido | extrair estilo, não copiar | ✅ com adaptação |
| Infinito sem cards definidos | definir + justificar | ❌ |
| Prompts genéricos | especificar | ❌ |
| Copy alterada sem permissão | reverter | ❌ |
| Contador no Card 1 | remover | ❌ |
| Múltiplos CTAs | manter 1 | ❌ |
| Exemplo violando proibição absoluta | corrigir o exemplo | ❌ |
| Hook fora do banco/aliases | mapear para tipo real | ❌ |

---

## FINAL GATE (antes de qualquer saída ao usuário)

- Estou entregando apenas o que esta etapa permite? Preciso aguardar aprovação?
- Algum dado inventado? (não) · Conflito com etapas anteriores? (não) · Estado de sessão atualizado?
- O usuário consegue agir com o que entreguei? A resposta é direta e sem enrolação?
