# Revisão da planilha PCM — Excel 2024

O cálculo automático foi ativado. As nove guias originais continuam visíveis; o PAINEL PCM, os dados digitados, as jornadas e os formatos existentes foram preservados. Não foram adicionadas macros.

## Ajustes

- A otimização anterior foi mantida: buscas repetidas de sobreposição substituídas por ordenação/acumulação; retirada de DESLOC/OFFSET; somas limitadas às tabelas existentes; consultas do PCM limitadas ao trecho ativo.
- A fórmula de atendimento usa `SE(diferença<0;0;diferença)`, conserva dias inteiros e o formato `[h]:mm`. O caso de 22/05/2026 13:26 a 17/07/2026 09:00 corresponde a **1339:34**. MÁXIMO também calcula esse valor corretamente: o zero observado era um resultado sem atualização no modo manual.
- Horários de realização incompletos deixam a duração pendente. Durações com dias inteiros não são reduzidas ao resto de 24 horas.
- Critérios quebrados de SIM/PARCIAL foram corrigidos nos resumos antigos. O resumo administrativo consulta TURNO, em vez de SETOR. Os totais por turno consultam as OS diretamente.
- O MTBF dos resumos antigos considera tempo disponível menos manutenção e quantidade de falhas, em vez de dividir pelo total de OS. MTTR usa duração por falha. Capacidades incompatíveis produzem `REVISAR HORAS`, em vez de indicadores negativos.
- CALCULOS passou a cobrir a capacidade existente de **12.000 OS** (até a linha 12001 da MEMÓRIA), incluindo as OS recentes que estavam fora da antiga tabela auxiliar. Células sem OS são protegidas contra datas fictícias.
- Os relatórios diários usam a data real de finalização e unem intervalos independentemente da ordem das OS. A união é feita separadamente por linha ou máquina; eventos simultâneos em máquinas diferentes não se anulam. Paradas com vários dias são recortadas integralmente no dia e horário selecionados.
- A guia auxiliar CALC_REVISAO fica oculta e compartilha três ordenações entre os relatórios. Fórmulas repetidas são armazenadas como fórmulas compartilhadas para reduzir o tamanho do arquivo.

## Definições e pendências preservadas

O painel PCM considera OS do tipo MÁQUINA PARADA e usa o intervalo entre início e finalização da realização. Os relatórios diários originais mantêm seu critério `LINHA PARADA? = SIM` e o início na abertura da OS; agora usam a data real da realização no término. São definições diferentes, portanto os resultados podem diferir.

Quatro identidades de linha já estavam apagadas (`#REF!`) em RESULTADOS POR LINHAS: A4, A7, A9 e A16, com reflexos nos blocos de RESULTADOS POR TURNO. Não é possível reconstruir esses nomes com segurança nem atribuir suas horas cadastradas a outras linhas. Os cálculos dependentes mostram `REVISAR LINHA`; as referências originais foram preservadas para identificação. Os totais afetados devem ser interpretados como incompletos.

O resumo antigo POR MÁQUINA contém 137 máquinas, enquanto o catálogo tem 144. A lista original não foi reorganizada nem recebeu valores de jornada presumidos. O painel PCM mantém seu próprio cadastro.

Algumas OS possuem início anterior à abertura ou horários com dias inteiros. Os valores digitados foram preservados; os casos estão listados no relatório de revisão. A regra solicitada de atendimento retorna zero quando a diferença é negativa.

No relatório diário por turno, o tempo parado continua sendo a soma das uniões das linhas daquele turno. Isso representa horas de linhas, que podem exceder a duração do turno. Nesse caso, a disponibilidade mostra `REVISAR HORAS`; uma disponibilidade global exige definir a capacidade em horas de linhas.

As jornadas PCM continuam sendo estimativas uniformes por semana, sem feriados ou alterações históricas. Paradas do painel não são cortadas pelos horários de trabalho. Nenhuma entrada foi presumida para compensar dados faltantes.

## Verificação

Foram comparados os dados digitados, formatos, ordem e visibilidade das guias e o XML completo do PAINEL PCM com o arquivo recebido. Foram verificados o caso de 1339:34, 1000 horas exatas, diferença negativa, virada de meia-noite, horários ausentes e sobreposição. As expressões de ordenação foram executadas por um mecanismo de fórmulas independente; nos resumos diários, as variáveis LET foram substituídas por suas expressões antes da avaliação, pois esse mecanismo não resolve algumas dependências entre variáveis LET. Os resultados diários também foram comparados com uma união de intervalos calculada diretamente das OS.

Não há Excel instalado no ambiente de revisão: não foi medido o tempo real de recálculo no seu computador. O primeiro carregamento pede um recálculo completo para reconstruir as dependências; depois, o Excel pode usar cálculo incremental. O modo automático fica gravado no arquivo. Se outra planilha aberta impuser modo manual à sessão do Excel, selecione Fórmulas → Opções de Cálculo → Automático.
