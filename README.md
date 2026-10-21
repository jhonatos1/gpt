# Planilha de manutenção — PAINEL PCM

[Baixar a planilha atualizada](https://github.com/jhonatos1/gpt/raw/refs/heads/main/Planilha_PCM.xlsx)

Abra no Excel 2019 ou Microsoft 365. O painel usa fórmulas e listas de seleção, sem macros.

1. Em **PAINEL PCM**, escolha a máquina em **B4** e o período em **B6 / D6**.
2. Na tabela abaixo dos cartões, localize a máquina pelo filtro da coluna A.
3. Informe **horas por semana + dias por semana**, ou **dias + início + fim + intervalo diário**. Horas semanais informadas têm prioridade.
4. **Paradas OS**, na coluna G azul, é automática. Não digite paradas novamente. Consulte os indicadores nos cartões.

Exemplo de cadastro, sem alterar os dados entregues: 40 horas/semana e 5 dias = 8 horas/dia, de segunda a sexta. A planilha conta os dias correspondentes entre as datas, inclusive semanas incompletas. Com horários, considera turnos que passam da meia-noite e desconta o intervalo em minutos.

A jornada representa uma previsão uniforme: 5 dias = seg–sex, 6 = seg–sáb, 7 = todos os dias. Não desconta feriados, férias ou mudanças históricas de escala. Nenhuma jornada foi presumida para as máquinas: preencha os valores reais.

As paradas automáticas vêm das OS **MÁQUINA PARADA**, incluindo as marcadas como falha operacional. O intervalo usa **data da realização J, início K e finalização M**, com ajuste para meia-noite. A planilha une intervalos simultâneos para não contar o mesmo tempo duas vezes e considera apenas o trecho entre as datas **B6 / D6**, inclusive quando o evento começou antes do período. OS sem horários devem ser revisadas na fonte; não são substituídas por zero.

O painel acompanha **MTBF, MTTR, confiabilidade, corretiva/preventiva, disponibilidade e Índice de Saúde PCM**. OEE e seus campos de produção foram removidos. Basta cadastrar a jornada; os registros de manutenção vêm das OS.

MTBF e disponibilidade usam **horas previstas pela jornada menos as paradas registradas nas OS**. São estimativas: os intervalos de realização não incluem necessariamente espera desde a abertura nem perdas sem OS, e não são cortados pelos horários do turno ou do intervalo. Horas paradas maiores que as horas previstas bloqueiam o cálculo para revisão.

**Saúde PCM** é uma nota gerencial proposta de 0 a 100, calculada somente com MTBF, MTTR, percentual de preventiva e disponibilidade. Cada componente recebe uma nota limitada a 100% da sua meta; para MTTR, menor é melhor. As quatro notas têm pesos iguais inicialmente. Metas sugeridas: MTBF 100 h, MTTR 2 h, preventiva 80% e disponibilidade 95%, editáveis em **PCM_PARAMETROS**. Não são padrões obrigatórios nem uma medição física da condição da máquina. Sem dados suficientes, o índice fica pendente; não depende de dados de produção.

As OS continuam em **MEMÓRIA**. Todas as nove guias originais permanecem visíveis. Somente as novas guias auxiliares PCM ficam ocultas; use **Reexibir** no Excel para consultar seus cálculos e parâmetros avançados. A leitura automática de OS vai até a linha 12001 de MEMÓRIA.
