# Planilha de manutenção — PAINEL PCM

[**Baixar a planilha revisada com cálculo automático**](https://github.com/jhonatos1/gpt/raw/refs/heads/main/Planilha_PCM_Revisada.xlsx)

Versão para **Excel 2024**, baseada no último arquivo enviado. Todas as nove guias originais continuam visíveis. O PAINEL PCM, os dados digitados, as jornadas, os formatos e suas alterações foram preservados. Sem macros.

O cálculo está em **Automático**: novas OS e alterações passam a atualizar os indicadores sem exigir F9. Se outra planilha aberta colocar a sessão do Excel em modo manual, selecione **Fórmulas → Opções de Cálculo → Automático**.

Foram revisadas todas as guias, incluindo MEMÓRIA, CALCULOS, os relatórios e os auxiliares PCM. A revisão mantém a otimização das sobreposições e a retirada de DESLOC/OFFSET, corrige critérios dos resumos, amplia CALCULOS para a capacidade existente de 12.000 OS e compartilha ordenações entre os relatórios diários. O arquivo ficou aproximadamente 19% menor que o anexo recebido; o tempo real de recálculo no Excel não foi medido.

A duração de atendimento conserva períodos acima de 1.000 horas, com negativos iguais a zero e formato `[h]:mm`. O exemplo informado retorna **1339:34**. O zero anterior ocorria porque o cálculo estava em modo manual; MÁXIMO não limita a duração.

[**Ver ajustes, verificações e pendências da revisão**](REVISAO_PCM.md). Quatro nomes de linha já estavam apagados nos resumos antigos; os casos dependentes foram sinalizados para revisão. Os nomes e os dados de jornada não foram presumidos. O resumo antigo POR MÁQUINA também tem sete máquinas a menos que o catálogo; sua lista foi preservada.

## Como usar

1. Em **PAINEL PCM**, escolha a máquina em **B4** e as datas em **B6 / D6**.
2. Na tabela abaixo dos cartões, use o filtro da coluna A para localizar a máquina.
3. Informe horas por semana e dias por semana, ou dias e início/fim/intervalo diário. Horas semanais informadas têm prioridade.
4. Insira as OS em **MEMÓRIA**, dentro da capacidade atual de leitura até a linha **12001**. As paradas do painel são calculadas automaticamente a partir das OS **MÁQUINA PARADA**.

O painel mostra MTBF, MTTR, confiabilidade, corretiva/preventiva, disponibilidade e Índice de Saúde PCM. OEE e campos de produção continuam removidos.

As jornadas são previsões uniformes por semana, sem desconto de feriados e sem alterações históricas de escala. As paradas PCM usam a data/início/fim da realização, unem intervalos simultâneos e recortam o período escolhido; não são cortadas pelos horários da jornada. Dados insuficientes ou capacidades incompatíveis precisam de revisão na fonte.

Saúde PCM é uma nota gerencial proposta de 0 a 100, com metas e pesos editáveis em PCM_PARAMETROS. Não representa uma medição física da máquina. As guias auxiliares permanecem ocultas e podem ser reexibidas para consulta.

Versões anteriores: [otimizada em modo manual](https://github.com/jhonatos1/gpt/raw/refs/heads/main/Planilha_PCM_Otimizada.xlsx) · [versão anterior](https://github.com/jhonatos1/gpt/raw/refs/heads/main/Planilha_PCM.xlsx).
