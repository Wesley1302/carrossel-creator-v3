# Worked Example — Capa Editorial Food (a partir de referência)

Exemplo canônico de saída da Etapa F quando o usuário envia uma imagem de referência. Padrão-ouro de tom, profundidade e estrutura. **Este exemplo cumpre todas as regras da skill** — em especial: Card 1 sem contador, JSON no schema de REF_07, A-Editorial (comida, sem pessoa realista).

## Input do usuário

> "Achei essa capa de carrossel no Instagram (fundo branco limpo, headline serifada itálica '5-minute breakfasts', um ovo frito flutuando abaixo, cabeçalho pequeno com marca e nome da série). Gera o prompt JSON pra recriar esse estilo pra minha marca 'Grow with Alex'."

## Saída da skill

### Análise (Visual Teardown resumido)

Capa editorial de revista de comida: divisão minimalista entre display serif itálico dramático e um único objeto-herói flutuante. Composição sustentada por espaço negativo extremo — fundo branco puro, sem prato ou superfície, sombra suave sugerindo luz difusa superior. Sistema de cabeçalho (marca à esquerda, série à direita) cria a arquitetura da série. Decisões-chave: ovo hiper-real com gema vívida como único ponto focal, terço superior dominado por negativo, serif itálico como voz da marca. **Nota de conformidade:** a referência original trazia contador "1/7" na capa — removido, porque Card 1 nunca leva contador; o contador entra a partir do Card 2 da série.

### Prompt JSON — Card 1 (capa)

```json
{
  "card": 1,
  "role": "HOOK (cover)",
  "canvas": { "size": "1080x1350", "orientation": "portrait", "safe_area_px": 80 },
  "path": "A",
  "path_substyle": "A-Editorial (food hero, intentional editorial aesthetic)",
  "style": {
    "rendering": "editorial food magazine cover, minimalist floating hero object, hyperrealistic food photography with crisp typography",
    "atmosphere": "clean, appetizing, premium-casual",
    "background": "pure seamless white #FFFFFF, no plate or surface"
  },
  "palette": {
    "primary": { "hex": "#0A0A0A", "function": "headline (near-black, slightly tinted)" },
    "secondary": { "hex": "#1E3A5F", "function": "running header text" },
    "accent": { "hex": "#F59E0B", "function": "yolk tone echoed as brand accent" }
  },
  "typography": {
    "display": "high-contrast italic serif (Bodoni Moda feel), elegant editorial",
    "support": "small bold sans-serif for running header",
    "weight_contrast": "display dominates; header is quiet system furniture"
  },
  "text_blocks": [
    { "role": "brand header", "exact_visible_text": "Grow with Alex", "position": "top-left, within safe area", "color": "#1E3A5F", "relative_size": "small" },
    { "role": "series header", "exact_visible_text": "5-Minute Breakfasts", "position": "top-right, within safe area", "color": "#1E3A5F", "relative_size": "small" },
    { "role": "headline", "exact_visible_text": "5-minute\nbreakfasts", "position": "centered upper-middle third, second line dramatically larger", "color": "#0A0A0A", "relative_size": "huge" },
    { "role": "tagline", "exact_visible_text": "Fast mornings, real food, zero compromise", "position": "bottom-center, within safe area", "color": "#4A5568", "relative_size": "small italic" }
  ],
  "subject": "single photorealistic sunny-side-up fried egg, vivid orange-yellow yolk dome with subtle sheen, crispy golden-brown ruffled edges, natural irregular shape, floating cut-out style with soft natural shadow beneath",
  "camera": { "focal_length": "85mm", "aperture": "f/8", "depth_of_field": "deep — egg fully sharp", "angle": "slight three-quarter overhead" },
  "lighting": { "source": "soft overhead studio diffusion", "quality": "gentle highlight on yolk dome", "shadows": "single soft contact shadow beneath egg" },
  "composition": { "hierarchy": "headline > hero egg > headers > tagline", "subject_placement": "egg centered lower-middle, ~35% of frame height", "negative_space": "generous around headline and hero" },
  "legibility": { "min_contrast": "4.5:1", "text_protection": "pure white background behind all text", "critical_text_within_safe_area": true },
  "quality": {
    "include": ["hyperreal egg texture", "vivid natural yolk colour", "crisp italic serif rendering", "soft natural food shadow", "editorial magazine finish", "precise small header typography"],
    "avoid": ["warped or misspelled text", "extra text not specified", "slide counter on this card", "visible plate or pan", "harsh reflections", "cartoonish rendering", "neon yolk colour", "duplicate eggs"]
  },
  "reference_standard": "Bon Appétit / Kinfolk food photography meets minimalist editorial cover"
}
```

### Nota de sistema (para os próximos cards da série)

A partir do Card 2: adicionar `"counter": { "exact_visible_text": "2/7", "position": "top-right corner", "opacity": "40-70%", "size": "small, discrete" }` e travar palette/typography idênticos (Locked Visual System de REF_07).

### Variações úteis

1. **Versão moody** — fundo aubergine profundo #2A1F2E, headline creme #F4ECDC, luz lateral dramática. Mesma composição, mood oposto — testa a consistência do layout entre paletas.
2. **Outro herói** — trocar o ovo por avocado toast, bowl de granola ou pilha de panquecas. Testa a flexibilidade do sistema.
3. **Post avulso** — se não for capa de série, remover os headers de série; capa mais limpa.
