# Planilha de manutenção — PAINEL PCM

[Baixar a planilha atualizada](https://github.com/jhonatos1/gpt/raw/refs/heads/main/Planilha_PCM.xlsx)

Abra no Excel. O painel usa fórmulas e listas de seleção, sem macros.

1. Em **PAINEL PCM**, escolha a máquina em **B4** e o período em **B6 / D6**.
2. Na tabela abaixo dos cartões, localize a máquina pelo filtro da coluna A.
3. Informe **horas por semana + dias por semana**, ou **dias + início + fim + intervalo diário**. Horas semanais informadas têm prioridade.
4. Consulte MTBF, MTTR, confiabilidade, corretiva/preventiva, OEE e Saúde PCM nos cartões.

Exemplo de cadastro, sem alterar os dados entregues: 40 horas/semana e 5 dias = 8 horas/dia, de segunda a sexta. A planilha conta os dias correspondentes entre as datas, inclusive semanas incompletas. Com horários, considera turnos que passam da meia-noite e desconta o intervalo em minutos.

A jornada representa uma previsão uniforme: 5 dias = seg–sex, 6 = seg–sáb, 7 = todos os dias. Não desconta feriados, férias ou mudanças históricas de escala. Nenhuma jornada foi presumida para as máquinas: preencha os valores reais.

Para OEE, preencha paradas totais em horas, produção total, produção boa e ciclo ideal em segundos por unidade. As datas desses totais ficam em **B27 / D27**; se não coincidirem com o período do painel, os totais são ignorados. Ao trocar o período dos apontamentos, substitua os valores G–I de todas as máquinas. A tabela não mantém histórico desses totais.

Sem paradas totais apontadas, o MTBF usa uma **estimativa pela jornada menos reparos das OS**. Isso não substitui horas efetivamente medidas; a origem aparece no rodapé do painel. OEE não é presumido a partir da jornada. Saúde PCM é um índice gerencial proposto, com metas e pesos editáveis nas guias auxiliares.

As OS continuam em **MEMÓRIA**. Todas as nove guias originais permanecem visíveis. Somente as novas guias auxiliares PCM ficam ocultas; use **Reexibir** no Excel para consultar seus cálculos e parâmetros avançados. A leitura automática de OS vai até a linha 12001 de MEMÓRIA.
