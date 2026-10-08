# Pede Simininu: instruções para o Claude

## Perguntas de números: skills de dados + cofre do Obsidian

Uma "pergunta de números" é qualquer pergunta sobre vendas, faturamento, metas, PDVs, clientes, produtos, campanhas (Meta Ads, Google Ads), Instagram, site ou outra métrica da Pede Simininu. Quando o usuário fizer uma, siga estes passos sem precisar que ele peça:

1. **Contexto no cofre (conector "Obsidian Pede Simininu").** Comece com `ler_nota("index.md")` e depois leia o que se aplica:
   - `entities/pede-simininu.md`: empresa, números e prioridades
   - `decisoes/2026-09-25-meta-pdvs-e-sistema-lynces.md`: meta de 2026 e PDVs
   - `entities/produtos/produtos.md`: catálogo
   - `entities/clientes-e-canais.md`: canais e clientes
   - `relatorios/instagram/` (o mais recente): para perguntas de Instagram
   - `buscar(<termo>)`: para qualquer outro assunto

   Em cada informação tirada do cofre, cite a nota de onde ela veio.
2. **Fonte dos números.** Siga a hierarquia de fontes do `SCHEMA.md`:
   - Lynces, quando existir.
   - Decisões registradas.
   - Exportação do Mercos ou do Omie enviada pelo dono, com data.
   - Dados ao vivo de anúncios, GA4, Instagram e Shopify vêm do conector Windsor.ai.
   - Números do laudo de set/2026 e do Power BI são **históricos**: cite sempre com a data.
   - Inferência sua vai marcada como **[HIPÓTESE]**.
   - Se o número não está no cofre nem nas fontes, diga isso. Não invente.
3. **Análise com as skills de dados** (`.claude/skills/`):
   - `/analyze` para a pergunta em si
   - `/explore-data` quando chegar uma tabela ou arquivo novo
   - `/write-query` quando precisar de SQL
   - `/create-viz` ou `/build-dashboard` quando um gráfico ou painel ajudar
   - `/validate-data` antes de entregar uma análise que será mostrada a alguém (conselho, diretor, equipe)
4. **Registro no cofre.** O conector só escreve na Caixa de entrada. Ao terminar, crie uma nota com `criar_nota_caixa_entrada`. O corpo não leva frontmatter e começa assim:
   - linha 1: `destino: <pasta do SCHEMA>`. Análise respondida vai para `queries/`, relatório de Instagram para `relatorios/instagram/`, número que muda uma decisão para `decisoes/`.
   - linha 2: `secao: <seção ou nota canônica de destino>`
   - depois, o resultado: pergunta, resposta, números com fonte e data, e as pendências.

## Sigilo
Nunca leia, cite ou registre resultado por vendedor, salários, devedores ou acessos. Esses dados são de `sigilo: alto` no cofre. Se a pergunta depender deles, diga que o dado é sigiloso e não está disponível pelo conector.
