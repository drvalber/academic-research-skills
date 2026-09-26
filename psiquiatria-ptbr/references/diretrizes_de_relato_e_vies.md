# Diretrizes de relato, risco de viés e certeza da evidência

Referência da camada `psiquiatria-ptbr`. Serve à escrita (`academic-paper`), à revisão
simulada (`academic-paper-reviewer`) e à síntese (`deep-research`). As versões citadas
devem ser conferidas na rede EQUATOR (equator-network.org) no momento do uso, porque
checklists são atualizados.

---

## 1. Qual checklist usar

| Desenho do estudo | Diretriz de relato | Uso na skill |
|---|---|---|
| Ensaio clínico randomizado | **CONSORT** (versão vigente; houve atualização em 2025 que incorporou itens de danos e de transparência) | Escrita e revisão de ECR |
| Protocolo de ensaio | **SPIRIT** (versão vigente) | Protocolos para registro e CEP |
| Revisão sistemática e metanálise | **PRISMA 2020** + **PRISMA-S** (busca) + **PRISMA-P** (protocolo) | Modo `systematic-review` |
| Metanálise de observacionais | **MOOSE** | Complementa PRISMA |
| Coorte, caso-controle, transversal | **STROBE** | Estudos de prontuário e epidemiológicos |
| Acurácia diagnóstica | **STARD 2015** | Validação de escalas e rastreio |
| Modelo de predição (inclusive com IA) | **TRIPOD+AI** | Modelos prognósticos, aprendizado de máquina |
| Relato de caso | **CARE** | Casos clínicos (ver ética no Brasil) |
| Pesquisa qualitativa | **COREQ** (entrevistas e grupos) ou **SRQR** | Burnout, espiritualidade, experiência do paciente |
| Descrição da intervenção | **TIDieR** | Obrigatório na prática para psicoterapias (TIP, TCC) |
| Avaliação econômica | **CHEERS 2022** | Custo-efetividade |
| Diretriz clínica | **AGREE II** (avaliação) e **RIGHT** (relato) | Leitura crítica de diretrizes |
| Melhoria de qualidade | **SQUIRE 2.0** | Projetos em serviço |

Regra da skill: todo manuscrito tem **um** checklist principal declarado na seção de
Métodos e entregue preenchido (item → página/linha) como material suplementar.

---

## 2. Risco de viés por desenho

| Desenho | Ferramenta | Domínios que mais pesam em psiquiatria |
|---|---|---|
| ECR | **RoB 2** | Desvios da intervenção pretendida (cegamento quebrado), dados faltantes (abandono alto), mensuração do desfecho (avaliador ciente do grupo em escalas heteroaplicadas) |
| Estudos não randomizados de intervenção | **ROBINS-I** (conferir a versão vigente) | Confusão por indicação, seleção, desvios da intervenção |
| Estudos de exposição | **ROBINS-E** | Confusão, mensuração da exposição |
| Observacionais (alternativa simples) | Newcastle-Ottawa | Aceita por periódicos, mas menos rigorosa; preferir ROBINS quando possível |
| Acurácia diagnóstica | **QUADAS-2** | Viés de espectro, padrão de referência não cego |
| Revisões sistemáticas | **AMSTAR 2** | Protocolo prévio, busca abrangente, avaliação de viés dos incluídos |
| Modelos de predição | **PROBAST** (conferir versão com IA) | Sobreajuste, validação externa ausente |

A avaliação é feita por desfecho, não por estudo, quando o RoB 2 é usado.

---

## 3. Certeza da evidência: GRADE

Partida: ECR começam em **alta**; observacionais, em **baixa**.

Rebaixam: risco de viés, inconsistência, evidência indireta, imprecisão, viés de publicação.
Elevam (só observacionais): efeito grande, gradiente dose-resposta, confundimento
residual que atuaria contra o efeito observado.

Saída obrigatória em revisão sistemática: **tabela "Resumo dos achados"** por desfecho
crítico, com efeito relativo, efeito absoluto por 1.000 pacientes e certeza.

Linguagem associada à certeza (para o texto em português):

| Certeza | Formulação sugerida |
|---|---|
| Alta | "X reduz..." |
| Moderada | "X provavelmente reduz..." |
| Baixa | "X pode reduzir..." |
| Muito baixa | "O efeito de X sobre ... é muito incerto." |

Essa escala se alinha à escada de força de afirmação do núcleo
(`shared/references/claim_strength_ladder.md`); em caso de conflito, prevalece a regra
mais conservadora.

---

## 4. Pontos críticos de metodologia específicos da psiquiatria

A revisão simulada (`academic-paper-reviewer`, sobretudo `methodology-focus`) deve
verificar, quando aplicável:

1. **Definição operacional do diagnóstico**: critérios (DSM-5-TR ou CID-11), instrumento
   (entrevista estruturada: SCID-5, MINI, DIVA-5) e quem aplicou.
2. **Definição de resistência ao tratamento**: número de tentativas adequadas, dose e tempo
   mínimos, como a adequação foi verificada (prospectiva ou retrospectiva, por exemplo
   com instrumento como o ATHF ou o MGH-ATRQ). "Resistente" sem critério explícito é
   falha de relato.
3. **Desfecho primário pré-especificado** e coincidente com o registro do ensaio
   (troca de desfecho é achado de revisão).
4. **Resposta e remissão** com limiar explícito e referência ao limiar adotado
   (ver `escalas_e_desfechos.md`).
5. **Dados faltantes**: abandono por braço, motivo, e método de análise (MMRM ou imputação
   múltipla; LOCF isolado é inadequado como análise primária).
6. **Integridade do cegamento**: avaliada ou não; avaliador de desfecho independente do
   prescritor.
7. **Resposta ao placebo e período de *lead-in***: presença de *washout* ou *placebo
   lead-in* e seu efeito sobre a amostra.
8. **Segurança**: ideação e comportamento suicida monitorados com instrumento estruturado
   (C-SSRS), virada maníaca em bipolares, eventos adversos com denominador e gravidade.
9. **Comorbidades e medicações concomitantes**: permitidas ou não, e como foram controladas.
10. **Generalização**: critérios de exclusão amplos (suicidalidade, uso de substâncias,
    comorbidade clínica) limitam a aplicação a casos complexos da prática real.
11. **Psicoterapias**: manualização, fidelidade ao protocolo, formação e supervisão dos
    terapeutas, controle com atenção equivalente (TIDieR).
12. **Farmacogenética**: genes e alelos testados, fenótipo metabolizador atribuído,
    diretriz de interpretação (CPIC ou DPWG, com versão) e desenho que isole o efeito do
    teste (teste guiado versus tratamento usual cego ao resultado).

---

## 5. Integração com o núcleo

- O modo `systematic-review` de `deep-research` já produz relatório PRISMA 2020; esta
  camada acrescenta o conjunto de bases, RoB 2/ROBINS e GRADE em português.
- O modo `methodology-focus` de `academic-paper-reviewer` recebe a lista da seção 4
  como critérios adicionais do domínio. Ela soma critérios, não retira nenhum.
- Nada aqui substitui as barreiras de integridade (Stage 2.5 e 4.5) do pipeline.
