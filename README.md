# Planilha de manutenção — PAINEL PCM

[Baixar a planilha otimizada](https://github.com/jhonatos1/gpt/raw/refs/heads/main/Planilha_PCM_Otimizada.xlsx)

**Versão otimizada do arquivo enviado em 21/10/2026.** Dados, layout, guias, formatações, configurações do painel e alterações nas células da MEMÓRIA foram preservados. O painel e a MEMÓRIA permanecem integralmente iguais ao anexo; a otimização está nas fórmulas auxiliares e de resumo.

- As buscas repetidas das paradas foram substituídas por ordenação e acumulação dos intervalos, mantendo a contagem sem duplicar sobreposições.
- Foram retiradas 18.340 chamadas voláteis de `OFFSET`/`DESLOC`, substituídas por referências equivalentes à linha anterior.
- Consultas de soma usam as tabelas existentes; resumos consultam o intervalo ativo. Contagens de colunas inteiras foram preservadas quando contar células vazias poderia mudar seu significado.
- O arquivo ficou aproximadamente 29% menor. Isso mede tamanho do arquivo; o tempo real de recálculo no Excel não foi medido.

O **modo de cálculo manual foi mantido**, como estava no arquivo enviado: pressione **F9** para atualizar. A opção de forçar um recálculo completo foi retirada para permitir atualização incremental. Não há macros. A ordenação usa `SORTBY`, disponível no Excel 2021/Microsoft 365; o arquivo já usava funções dessa geração, como `XLOOKUP`.

Os resultados substituídos foram comparados nas 12 mil linhas auxiliares, e as expressões de ordenação e os casos de sobreposição foram avaliados separadamente. Células com erros de referência que já existiam foram preservadas, sem alterar regras ou substituir erros por zero. [A versão anterior permanece disponível](https://github.com/jhonatos1/gpt/raw/refs/heads/main/Planilha_PCM.xlsx).

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
