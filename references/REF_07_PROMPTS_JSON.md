# REF_07: PROMPTS JSON POR CARD (Etapa F) + CAMADA DE REALISMO

Transforma copy aprovada + direção visual aprovada em **1 JSON válido por card**, em inglês, pronto para colar em IA de imagem (GPT Image, Flux, Midjourney, Imagen etc.).
Copy aprovada permanece intocada, sempre em `exact_visible_text`. **Pré-condições (nesta ordem, sem pular):** estratégia → quantidade confirmada → copy aprovada → visual aprovado → modo (quadro a quadro/infinito) escolhido.

---

## SCHEMA JSON CANÔNICO

Todo card usa este schema. Campos irrelevantes para o caminho são omitidos (não deixar vazios).

```json
{
  "card": 2,
  "role": "PROBLEMA (re-hook)",
  "canvas": { "size": "1080x1350", "orientation": "portrait", "safe_area_px": 80 },
  "path": "B",
  "style": {
    "rendering": "flat 2D graphic design, vector-crisp typography",
    "atmosphere": "direct, professional, warm-neutral",
    "background": "off-white #FAF9F6, solid"
  },
  "palette": {
    "primary": { "hex": "#1A3A52", "function": "headlines, authority" },
    "accent": { "hex": "#E8630A", "function": "action, CTA highlights" },
    "neutral": { "hex": "#4A5568", "function": "body text" }
  },
  "typography": {
    "display": "condensed sans-serif, extra bold",
    "body": "sans-serif regular",
    "weight_contrast": "display at least 2x visual weight of body"
  },
  "text_blocks": [
    {
      "role": "headline",
      "exact_visible_text": "Você tá fazendo igual à maioria.",
      "position": "upper-left, off-axis",
      "color": "#1A3A52",
      "relative_size": "large"
    },
    {
      "role": "body",
      "exact_visible_text": "Mandando mensagem em massa, esperando alguém responder.\nSpoiler: não funciona.",
      "position": "center-left",
      "color": "#4A5568",
      "relative_size": "medium"
    }
  ],
  "graphic_elements": [
    { "element": "oversized numeral '01'", "treatment": "8% opacity, bleeding off top-right edge, decorative only, never under text" }
  ],
  "counter": { "exact_visible_text": "2/7", "position": "top-right corner", "opacity": "40-70%", "size": "small, discrete" },
  "composition": { "hierarchy": "headline > body > accent > counter", "asymmetry": "text block shifted left of center axis", "negative_space": "generous right column" },
  "legibility": { "min_contrast": "4.5:1", "text_protection": "solid background", "critical_text_within_safe_area": true },
  "quality": {
    "include": ["crisp text rendering", "consistent visual system", "mobile legibility"],
    "avoid": ["warped or misspelled text", "colored side border stripe", "gradient text", "glassmorphism", "extra text not specified", "counter on card 1"]
  }
}
```

**Regras do schema:**
- Todo texto visível SÓ existe dentro de `exact_visible_text`, com quebras de linha `\n` conforme copy aprovada. Nunca traduzir, adaptar ou acrescentar texto.
- `quality.avoid` sempre inclui "warped or misspelled text" e "extra text not specified".
- Card 1: sem objeto `counter` (omitir o campo por completo).
- 1 JSON por card, todos com o mesmo `palette`/`typography` (sistema travado).
- Se o gerador do usuário preferir prosa: converter o JSON em parágrafos mantendo todos os campos — mas o padrão de entrega é JSON.

### Sistema Travado (obrigatório em carrosséis de 5+ cards)
Antes do primeiro JSON, apresentar um bloco `locked_visual_system` (palette, typography, layout rules, counter style, atmosphere, recurring elements). Cada JSON referencia esses valores idênticos — é isso que garante consistência entre gerações independentes.

---

## ROTEADOR: CAMINHO A, B OU C (classificar cada card antes de gerar)

### Caminho A — Fotográfico (`"path": "A"`)
Pessoa, produto, comida, objeto, ambiente, cena. Acrescentar ao schema:

```json
"camera": { "focal_length": "…", "aperture": "…", "angle": "…", "depth_of_field": "…" },
"lighting": { "source": "…", "quality": "…", "shadows": "…" }
```

**Decisão obrigatória — subestilo:**
- **A-Realista** (pessoa/objeto/lugar que deve parecer FOTO REAL de celular): aplicar a CAMADA DE REALISMO abaixo. PROIBIDO: 85mm/50mm portrait, studio lighting, "commercial photography", "cinematic", "8k", "professional".
- **A-Editorial** (produto/comida em estética editorial intencional, sem pessoa realista): 85mm, f/8, luz de estúdio difusa etc. são permitidos.
Regra de decisão: se o card precisa parecer capturado da vida real → A-Realista. Se precisa parecer produção editorial assumida → A-Editorial. Na dúvida com pessoa: sempre A-Realista.

Sempre em A: `text_blocks` com proteção declarada (overlay 50-70%, blur, espaço negativo), text zone fora de rosto/mãos/textura complexa, safe area 80px.

### Caminho B — Tipográfico (`"path": "B"`)
Texto/layout protagonista, fundo sólido/gradiente sutil, shapes, flat design. **Zero linguagem de câmera** (sem focal length, aperture, bokeh, depth of field, cinematic). `style.rendering`: "flat 2D graphic design, vector-crisp typography, layout grid".

### Caminho C — Infinito panorâmico (`"path": "C"`)
2-3 cards consecutivos conectados. Um único JSON panorâmico + instruções de corte.

**Canvas (fonte canônica destas specs):**
- 2 cards: **2160x1350px** → corte em x:0-1080 e x:1080-2160
- 3 cards: **3240x1350px** → corte em x:0-1080, x:1080-2160, x:2160-3240
- Cada fatia final: 1080x1350 sem redimensionar.
- **Fallback** (gerador só aceita proporção padrão): 16:9 (2 cards) ou 21:9 (3 cards) — declarar explicitamente como aproximação que exige ajuste manual no editor. Nunca afirmar que 16:9 corta direto em 1080x1350.

Estrutura do JSON panorâmico:

```json
{
  "cards": "4-5",
  "canvas": { "size": "2160x1350", "cut_slices": ["x:0-1080 = Card 4", "x:1080-2160 = Card 5"], "safe_area_px": "80 per zone, including 80px from each cut line" },
  "path": "C",
  "zones": [
    { "zone": "left (Card 4)", "background": "…", "text_blocks": [ … ], "counter": { "exact_visible_text": "4/7", "position": "top-right of this zone" } },
    { "zone": "right (Card 5)", "background": "…", "text_blocks": [ … ], "counter": { "exact_visible_text": "5/7", "position": "top-right of this zone" } }
  ],
  "panoramic_rules": {
    "no_visible_dividers": true,
    "elements_may_bleed_across_cuts": "decorative only",
    "text_never_crosses_cuts": true,
    "seamless_transition": "gradual color/shape transition marks the boundary visually without drawn lines"
  },
  "cutting_instructions": "Cut at x:1080. Each slice is a standalone 1080x1350 portrait card. No borders or cut marks in the generation."
}
```

Regras C: zero divisórias visíveis · decorativos podem cruzar cortes, texto crítico nunca · cada card funciona sozinho após o corte · contador por zona (Card 1 nunca tem, mesmo dentro de trecho infinito) · cards vizinhos ao trecho mantêm o sistema travado.

### Caso híbrido (foto + texto dominante)
Caminho A com extensão tipográfica: câmera/luz permitidos + regras fortes de text zone, overlay e hierarquia. Texto continua o elemento principal de comunicação.

---

## 📷 CAMADA DE REALISMO (para A-Realista)

**Princípio:** imagem de IA parece falsa quando o prompt pede perfeição. Realismo = foto rápida, celular na mão, luz disponível, textura natural, enquadramento casual. O objetivo não é imagem bonita demais — é imagem plausível.

### As 7 camadas
| Camada | Quebra o realismo | Corrigir no prompt |
|---|---|---|
| Pessoa | "perfect skin", "flawless", "beauty photography" | "natural skin texture", "visible pores", "subtle blemishes", "natural asymmetry" |
| Câmera | "8k", "cinematic", "ultra sharp", "professional camera" | "smartphone camera", "24-28mm equivalent", "handheld", "casual framing" |
| Pose | pose de modelo, olhar perfeito | "candid moment", "spontaneous pose", "amateur snapshot feeling" |
| Luz | "studio lighting", "HDR" | "natural window light", "available light", "uneven real-world illumination" |
| Cenário | ambiente perfeito, 3D-looking | "lived-in atmosphere", "believable clutter", "imperfect arrangement" |
| Textura | "sharp details", "polished render" | "subtle sensor noise", "mild compression artifacts", "realistic focus softness" |
| Imperfeições | ausência total | "flyaway hairs", "slight wrinkles", "natural skin variation" |

**Câmera:** principal 24-28mm equiv.; selfie 20-24mm. Incluir: "handheld smartphone, slight wide-angle distortion, casual composition, mild edge softness, imperfect exposure". **Não usar:** 85mm/50mm portrait, "professional lens", bokeh dramático.

### Blocos prontos para o JSON (A-Realista com pessoa)
```json
"subject": "realistic person captured naturally, authentic expression, natural asymmetry, subtle skin pores, fine facial texture, no beauty retouching",
"clothing": "everyday clothing, natural fabric texture, slight wrinkles, believable folds",
"pose": "spontaneous, candid moment, relaxed body language, amateur snapshot feeling",
"setting": "real-world environment, lived-in atmosphere, believable clutter, natural scale",
"camera": { "device": "modern smartphone, handheld", "focal_length": "24-28mm equivalent", "behavior": "slight wide-angle distortion, casual composition, imperfect exposure" },
"lighting": { "source": "natural or available light", "quality": "soft ambient, subtle uneven illumination, no studio lighting" },
"effects": "subtle smartphone processing, slight noise, mild compression artifacts, realistic autofocus softness",
"details": "visible pores, fine lines, flyaway hairs, uneven hair volume, imperfect clothing folds",
"quality": {
  "include": ["photorealistic", "lifelike", "smartphone photo realism", "candid amateur photo"],
  "avoid": ["perfect skin", "studio lighting", "cinematic look", "8k", "beauty filter", "airbrushed face", "plastic skin", "CGI render", "artificial symmetry", "over-sharpening", "perfect bokeh", "professional photography"]
}
```
Para objeto/lugar realista: mesmos princípios sem os campos de pessoa.

### Checklist A-Realista
- [ ] ≥3 termos positivos de realismo? Removeu "perfect/studio/cinematic/8k/professional"?
- [ ] Smartphone/handheld + 24-28mm? Luz natural/ambient? ≥1 imperfeição visível? Pose candid?
- [ ] Text zone declarada: "clear negative space area for text overlay in [position]" — texto nunca sobre pele/cabelo/detalhe complexo sem overlay?
Falhou algum → revisar antes de entregar.

---

## PRESERVAÇÃO (regras invioláveis)

1. **Copy:** exatamente como aprovada, em `exact_visible_text`, sem tradução/reescrita/acréscimo. Vale para headline, body, CTA, contador e texto em elemento gráfico.
2. **Visual:** paleta/tipografia/elementos exatos da direção aprovada. Ajustes técnicos permitidos: overlay/blur para legibilidade, ajuste de contraste. Nunca mudar paleta, estilo ou composição.
3. **Quantidade:** N prompts para N cards. Nem mais, nem menos.
4. **Contador:** Card 1 sem (omitir campo). Cards 2+ com "[N]/[TOTAL]", canto consistente, opacidade 40-70%, pill só se a direção aprovada usar.

---

## FORMATO DE ENTREGA

```
**Locked Visual System**
```json
{ …sistema travado… }
```

**Prompt — Card 1**
```json
{ …JSON do card… }
```

[… todos os cards; trecho infinito = 1 JSON panorâmico no lugar dos cards conectados …]

**Próximo passo:** Cole cada JSON no seu gerador de imagem. Gere, confira texto exato e consistência. Se o texto sair com erro de grafia, gere novamente ou reduza o texto do card — me avise que eu ajusto.
```

---

## ERROS A EVITAR

1. Traduzir/reescrever copy ("Salva esse post" → "Save this post" = erro grave).
2. Inventar texto, tagline ou emoji não aprovado.
3. Card extra ou faltante.
4. Contador no Card 1 / faltando em Cards 2+.
5. Camera language em Caminho B.
6. 85mm/studio/commercial em A-Realista (usar camada de realismo).
7. Prompt genérico sem cores, posições e textos específicos.
8. Texto sem proteção sobre fundo complexo.
9. Texto crítico fora da safe area ou cruzando linha de corte no infinito.
10. Divisórias visíveis no panorâmico.
11. Estilo mudando entre cards sem motivo (sistema travado existe para isso).
12. Copiar marca/logo/celebridade/personagem protegido.
13. JSON inválido (vírgulas soltas, aspas não fechadas) — validar mentalmente a sintaxe antes de entregar.

## CHECKLIST INTERNO

- [ ] 1 JSON válido por card (ou panorâmico por trecho)? Sintaxe correta?
- [ ] Todo texto visível em `exact_visible_text`, idêntico à copy aprovada?
- [ ] Caminho certo por card? A-Realista com camada de realismo completa?
- [ ] Canvas correto (1080x1350 / 2160x1350 / 3240x1350; fallback declarado)?
- [ ] Safe area, contraste, proteção de texto, contador, sistema travado?
- [ ] `quality.avoid` cobre as proibições absolutas da direção aprovada?
