# psiquiatria-ptbr — camada de português do Brasil e psiquiatria clínica

Adaptação feita neste fork (`drvalber/academic-research-skills`) sobre o
[Academic Research Skills](https://github.com/Imbad0202/academic-research-skills), de
Cheng-I Wu. Não faz parte do projeto original.

## O que é

Uma quinta skill que funciona como **camada**: não tem agentes nem modos próprios. Ela:

1. entende pedidos em português ("revisão sistemática", "revisar meu artigo", "recebi os
   pareceres", "traduzir e analisar este artigo");
2. escolhe a skill e o modo do núcleo que atendem ao pedido;
3. acrescenta o contexto de psiquiatria clínica e as convenções do português acadêmico;
4. não relaxa nenhuma barreira de integridade do núcleo (verificação de citações,
   auditoria de afirmações, checkpoints obrigatórios).

Por ser uma camada, o núcleo continua intacto e as atualizações do autor original podem
ser incorporadas ao fork com poucos conflitos.

## Conteúdo

| Arquivo | Assunto |
|---|---|
| `SKILL.md` | Roteamento português → núcleo, regras de idioma, regras de domínio |
| `references/fontes_e_estrategia_de_busca.md` | Bases (MEDLINE, Embase, PsycINFO, CENTRAL, LILACS, registros), PICO e variantes, MeSH/DeCS, esqueleto de busca |
| `references/diretrizes_de_relato_e_vies.md` | CONSORT, PRISMA, STROBE, STARD, CARE, TIDieR etc.; RoB 2, ROBINS, QUADAS-2, AMSTAR 2; GRADE; pontos críticos da psiquiatria |
| `references/escalas_e_desfechos.md` | Escalas de depressão, bipolaridade, ansiedade, TDAH, burnout, espiritualidade; resposta, remissão, tamanho de efeito |
| `references/glossario_e_nomenclatura.md` | DSM-5-TR, CID-11, NbN, linguagem não estigmatizante, glossário inglês → português, falsos cognatos |
| `references/redacao_academica_ptbr.md` | Estilo, números, resumo estruturado, força das afirmações, Vancouver e ABNT, fluxo de tradução com análise crítica |
| `references/etica_e_regulacao_brasil.md` | CEP/CONEP, TCLE/TALE, LGPD, ReBEC, relato de caso, capacidade decisória, modelo de texto para Métodos |
| `references/periodicos_alvo.md` | Periódicos brasileiros e internacionais por tema |

## Instalação

Pelo plugin, apontando para este fork:

```text
/plugin marketplace add drvalber/academic-research-skills
/plugin install academic-research-skills
```

Ou por link simbólico num projeto, junto com as quatro skills do núcleo, das quais a
camada depende:

```bash
git clone https://github.com/drvalber/academic-research-skills.git ~/academic-research-skills
cd /caminho/do/projeto && mkdir -p .claude/skills
for s in deep-research academic-paper academic-paper-reviewer academic-pipeline psiquiatria-ptbr; do
  ln -s ~/academic-research-skills/$s .claude/skills/$s
done
```

## Exemplos de pedido

- "Me ajude a formular uma pergunta de pesquisa sobre farmacogenética em depressão resistente."
- "Quero fazer uma revisão sistemática sobre escetamina na depressão resistente."
- "Revise meu artigo sobre TDAH em adultos antes da submissão."
- "Traduza e analise criticamente este ECR de psicoterapia interpessoal."
- "Recebi os pareceres do *Brazilian Journal of Psychiatry*; monte o roteiro de revisão."
- "Escreva o resumo estruturado em português e o *abstract* em inglês."

## Limitações conhecidas

- **Idioma do resumo:** o registro de pares de idioma do núcleo
  (`shared/output_language_pair.md`) ainda não tem português. A camada pede "EN only" ao
  núcleo e produz o Resumo em português como entrega adicional.
- **ABNT:** o formatador e a verificação determinística de citações do núcleo não cobrem
  ABNT. A camada formata, mas a checagem automática vale só para Vancouver, APA e os
  demais formatos do núcleo.
- **Acesso às bases:** Embase, PsycINFO e LILACS dependem das ferramentas disponíveis
  na sessão. Sem elas, a skill entrega a estratégia de busca e pede os resultados ao
  usuário, sem afirmar que consultou.
- **Validação:** a camada não tem avaliações (*evals*) próprias. O comportamento é
  definido por prompt e ainda não foi medido.

## Atualizar o fork com o projeto original

```bash
git remote add upstream https://github.com/Imbad0202/academic-research-skills.git
git fetch upstream
git merge upstream/main
```

O aviso de atualização que o plugin mostra ao iniciar a sessão compara a versão instalada
com a do projeto **original**. Quando ele aparecer, `/plugin update` sozinho não basta:
primeiro é preciso incorporar o original ao fork com os comandos acima.

Conflitos esperados, quando houver, ficam nas linhas de contagem de skills
(`.claude-plugin/*.json`, `MODE_REGISTRY.md`), na tabela de skills de
`.claude/CLAUDE.md` e em `scripts/check_data_access_level.py`.

## Licença

CC BY-NC 4.0, a mesma do projeto original: uso não comercial, com atribuição a
Cheng-I Wu pelo núcleo.
