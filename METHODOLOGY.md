# Metodologia

Como o conteúdo deste repositório foi levantado e verificado, e o que ainda está pendente.

## Escopo do manual (`index.html`)

O manual de referência (10 capítulos) cita cerca de 40 fontes, selecionadas por
leitura direta, não por revisão sistemática formal. Cada citação linka para o
DOI ou URL canônico da fonte. Serve como panorama de leitura guiada, não como
levantamento exaustivo da literatura.

## Bibliografia verificada (`references.bib`)

As 178 entradas em `references.bib` vêm de uma revisão sistemática em
andamento, conduzida em paralelo a este manual, com protocolo PRISMA 2020.

**O que já foi feito:**

- Busca em DBLP (6.901 registros) e arXiv (2.084 registros), 2020 a 2026.
- Duas famílias de string de busca: vocabulário de alucinação/factualidade
  (Arm A) e vocabulário de geração restrita/verificação formal (Arm B).
- Deduplicação e exclusão a nível de título (janela temporal, conteúdo
  puramente visual/multimodal, sentido clínico não relacionado a IA).
- Verificação bibliográfica individual de cada uma das 178 entradas: título
  conferido caractere a caractere, lista de autores, veículo, ano e DOI,
  contra DBLP ou Crossref. 154 entradas têm DOI; as 24 restantes (ICLR, ICML,
  NeurIPS, TMLR, um COLING, um workshop CEUR-WS) não emitem DOI e carregam a
  URL de registro da DBLP em seu lugar.

**O que ainda não foi feito — e por isso `references.bib` não deve ser lido
como "a bibliografia completa e triada" do tema:**

- Das 178 entradas, apenas 25 foram efetivamente citadas e lidas até agora
  (no manual e no plano de revisão). As outras 153 são candidatas retiradas
  da busca, verificadas bibliograficamente, mas **não lidas nem triadas por
  relevância**.
- 3.643 registros adicionais aguardam triagem por título e resumo — ainda não
  entraram nem como candidatos verificados.
- Nenhuma etapa de extração de dados, avaliação de risco de viés, ou síntese
  foi executada.

Consulte o protocolo completo, com todas as strings de busca, critérios de
inclusão/exclusão e o fluxo PRISMA atualizado, no projeto de origem:
`SLR Test/review/prisma_review_llm_hallucination.md` (fora deste repositório,
a ser publicado separadamente quando a triagem avançar).

## Como uma entrada chega a `references.bib`

1. Busca automatizada (DBLP + arXiv) com as strings do protocolo.
2. Deduplicação.
3. Exclusão a nível de título por regra explícita, não por julgamento caso a
   caso.
4. Para entradas efetivamente citadas em algum documento deste projeto:
   verificação manual de título, autoria, veículo, ano e DOI contra a fonte
   primária (DBLP/Crossref), mais leitura do resumo para confirmar que o
   artigo sustenta a afirmação a que está associado.

Uma entrada presente em `references.bib` sem uso citado em `index.html`
significa apenas que passou pelos passos 1 a 3: busca e verificação
bibliográfica, não leitura ou triagem de relevância.

## Convenções de citação

- Chaves DBLP (`DBLP:journals/csur/...`) são preferidas por serem estáveis e
  reverificáveis em `dblp.org/rec/<chave>`.
- Entradas fora da DBLP (blocos de método) usam chaves legíveis.
- Preprints sem registro peer-reviewed até a data de exportação estão listados
  no cabeçalho de `references.bib`.

## Atualização

Este arquivo e `references.bib` devem ser atualizados juntos sempre que uma
nova rodada de busca, triagem ou citação for incorporada. Registre a data da
mudança no cabeçalho de `references.bib`.
