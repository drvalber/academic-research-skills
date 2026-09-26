# Fontes e estratégia de busca em psiquiatria

Referência da camada `psiquiatria-ptbr`. Complementa, sem substituir, os protocolos de
busca e verificação de `deep-research` (em especial `bibliography_agent` e
`source_verification_agent`). Nenhuma regra deste arquivo relaxa uma verificação do núcleo.

---

## 1. Honestidade sobre o acesso às bases

As bases abaixo são as de referência na área. **Se a sessão não tiver ferramenta que
consulte uma base diretamente, a skill não finge que consultou.** Nesse caso ela:

1. entrega a string de busca pronta, por base, para o usuário executar;
2. pede que o usuário exporte os resultados (RIS, NBIB, CSV) ou cole os PMIDs/DOIs;
3. registra no relatório, em "Limitações da busca", quais bases foram consultadas pela
   sessão e quais foram consultadas pelo usuário.

Um relatório que diga "busca realizada no PubMed, Embase e PsycINFO" sem que isso tenha
acontecido é fabricação de método, um dos modos de falha que as barreiras de integridade
do pipeline bloqueiam.

---

## 2. Bases por finalidade

| Finalidade | Bases | Observações |
|---|---|---|
| Núcleo biomédico | **PubMed/MEDLINE** | Vocabulário MeSH; acesso livre. Base mínima obrigatória em qualquer revisão. |
| Farmacologia e ensaios europeus | **Embase** | Vocabulário Emtree; cobre congressos e periódicos europeus ausentes do MEDLINE. Acesso por assinatura (Portal CAPES). |
| Psicologia e psicoterapia | **APA PsycINFO** | Indispensável para TIP, TCC, intervenções psicossociais e espiritualidade. |
| Ensaios controlados | **Cochrane CENTRAL** e **CDSR** | CENTRAL para ensaios; CDSR para revisões Cochrane já publicadas (verificar antes de propor uma nova). |
| Produção latino-americana | **LILACS** (via BVS) e **SciELO** | Vocabulário DeCS. Essencial para dados brasileiros e para evitar viés de idioma. |
| Enfermagem e cuidado | CINAHL | Útil em temas de adesão, cuidado e saúde mental comunitária. |
| Registros de ensaios | **ClinicalTrials.gov**, **WHO ICTRP**, **ReBEC** | Identificam ensaios não publicados (viés de publicação) e desfechos trocados em relação ao protocolo. |
| Protocolos de revisão | **PROSPERO** | Verificar se já há revisão registrada sobre a mesma pergunta. |
| Preprints | medRxiv, PsyArXiv | Incluir só com rótulo explícito de "não revisado por pares" e em análise de sensibilidade. |
| Diretrizes clínicas | CANMAT, NICE, APA (American Psychiatric Association), WFSBP, BAP, RANZCP, ABP, Ministério da Saúde (PCDT) | Diretriz é fonte secundária: citar a recomendação e o nível de evidência que a própria diretriz atribui, e conferir a data da versão. |

Cobertura mínima recomendada para revisão sistemática em psiquiatria: MEDLINE + Embase +
PsycINFO + CENTRAL + LILACS + um registro de ensaios. Omissões precisam ser justificadas
em "Limitações".

---

## 3. Estruturação da pergunta

| Tipo de pergunta | Estrutura | Exemplo |
|---|---|---|
| Intervenção | **PICO(S)** — População, Intervenção, Comparador, Desfecho, (Desenho) | Adultos com depressão resistente ao tratamento / escetamina intranasal + antidepressivo oral / placebo + antidepressivo oral / remissão pela MADRS em 4 semanas / ECR |
| Exposição ou fator de risco | **PECO** | Adultos com TDAH / uso de estimulante / não uso / eventos cardiovasculares / coorte |
| Diagnóstico | **PIRD** — População, Teste-índice, Referência, Diagnóstico | Adultos em atenção primária / ASRS v1.1 / entrevista clínica estruturada (DIVA-5) / TDAH |
| Prognóstico | **PICOTS** ou **PFO** | Pacientes com primeiro episódio maníaco / fatores clínicos / recorrência em 2 anos |
| Qualitativa | **SPIDER** ou **PICo** | Médicos residentes / experiência de burnout / entrevistas / fenomenologia |
| Prevalência | **CoCoPop** — Condição, Contexto, População | Burnout / hospitais universitários brasileiros / médicos |

A skill deve devolver a pergunta ao usuário para confirmação antes de montar a busca.

---

## 4. Vocabulário controlado: MeSH, Emtree e DeCS

Regras de construção:

- Combinar **descritor controlado + termos livres** (título/resumo) para cada conceito.
- Conceitos diferentes ligados por `AND`; sinônimos do mesmo conceito ligados por `OR`.
- DeCS é trilíngue (português, espanhol, inglês) e segue o MeSH; para LILACS, usar os três
  idiomas nos termos livres.
- Evitar filtros de idioma e de data sem justificativa (viés de idioma).
- Documentar data da busca, número de registros por base e a string exata (PRISMA-S).

### Descritores MeSH úteis na área (conferir no MeSH Browser antes de usar)

| Conceito | MeSH | Observação |
|---|---|---|
| Depressão resistente | `Depressive Disorder, Treatment-Resistant` | Existe desde 2012; combinar com termos livres, pois estudos antigos não estão indexados nele. |
| Transtorno depressivo maior | `Depressive Disorder, Major` | |
| Transtorno bipolar | `Bipolar Disorder` | |
| TDAH | `Attention Deficit Disorder with Hyperactivity` | Adultos: combinar com `Adult` e termos livres "adult ADHD". |
| Ansiedade | `Anxiety Disorders`, `Anxiety` | O segundo é sintoma; o primeiro, transtorno. |
| Burnout | `Burnout, Professional`, `Burnout, Psychological` | |
| Espiritualidade | `Spirituality`, `Religion and Psychology`, `Religion and Medicine` | |
| Psicoterapia interpessoal | `Interpersonal Psychotherapy` | Conferir existência e data de entrada; complementar com termo livre "interpersonal psychotherapy". |
| Farmacogenética | `Pharmacogenetics`, `Pharmacogenomic Testing`, `Cytochrome P-450 CYP2D6`, `Cytochrome P-450 CYP2C19` | |
| Cetamina e escetamina | `Ketamine` | Escetamina costuma aparecer como termo livre ("esketamine"). |

> Os descritores acima são pontos de partida. A skill confere cada um na fonte oficial
> antes de usar e registra a versão do vocabulário.

### Esqueleto de estratégia (PubMed)

```
("Depressive Disorder, Treatment-Resistant"[Mesh] OR "treatment-resistant depression"[tiab]
   OR "treatment resistant depression"[tiab] OR "refractory depression"[tiab]
   OR "difficult-to-treat depression"[tiab])
AND
("Ketamine"[Mesh] OR ketamine[tiab] OR esketamine[tiab] OR "Spravato"[tiab])
AND
(randomized controlled trial[pt] OR randomized[tiab] OR randomised[tiab] OR placebo[tiab]
   OR "clinical trials as topic"[mesh:noexp] OR randomly[tiab] OR trial[ti])
```

O terceiro bloco é uma versão do filtro de alta sensibilidade da Cochrane para ECR no
PubMed. A skill deve citar a versão usada do filtro e não alterá-lo sem registrar a mudança.

---

## 5. Hierarquia de evidência e o que ela não diz

Para perguntas de intervenção, a ordem habitual é: revisões sistemáticas de ECR →
ECR → coortes → caso-controle → séries e relatos de caso → opinião. Em psiquiatria, três
ressalvas mudam essa leitura:

1. **Resposta ao placebo alta e crescente** em depressão e ansiedade reduz o tamanho de
   efeito observado; efeitos pequenos não significam ausência de efeito clínico.
2. **Quebra funcional do cegamento** em intervenções com efeito subjetivo evidente
   (cetamina, psicodélicos, estimulantes, EMT com sensação no couro cabeludo) infla o
   efeito; a skill deve procurar se o estudo avaliou a integridade do cegamento.
3. **Ensaios curtos**: 6 a 8 semanas é o padrão regulatório em depressão; conclusões
   sobre manutenção e recaída exigem ensaios de retirada randomizada ou seguimento longo.

A certeza da evidência final é graduada por **GRADE** (alta, moderada, baixa, muito baixa),
não pela posição do desenho na pirâmide.
