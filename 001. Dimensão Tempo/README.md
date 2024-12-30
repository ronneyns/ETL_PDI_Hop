# Dimensão Tempo

## Objetivo
Realizar a carga da dimensão Tempo para uso em um Data Warehouse, permitindo uma maior capacidade de estratificação de datas.

## Ferramenta
Apache Hop 2.9

## Processo
O processo gerará um conjunto de dados com vários atributos dentro do período de 30/12/1899 a 31/12/2099.

![Pipeline](dim_tem_tempo.png)

## Saída
Os campos resultantes são os seguintes:
- tem\_srk\_tempo: Chave única para identificar um data no conjunto de tempo especificado
- tem\_bsk\_tempo: Um data qualquer dentro do período especificado para a dimensão (por exemplo, 30/12/1899);
- tem\_str\_data\_dmy: Data como texto no formato DD/MM/YYYY (por exemplo, 30/12/1899);
- tem\_str\_data\_ymd: Data como texto no formato YYYY-MM-DD (por exemplo, 1899-12-30);
- tem\_str\_data_extenso: Descrição do dia por extenso (por exemplo, "Sábado, 30 de Dezembro de 1899");
- tem\_num\_dia: Dia do mês (valores de 1 a 31);
- tem\_str\_dia: Dia do mês como texto (valores de "01" a "31");
- tem\_num\_dia\_semana: Dia da semana (valores de 1 a 7);
- tem\_str\_dia\_semana: Dia da semana como texto (valores de "01" a "07");
- tem\_str\_dia\_semana_sigla: Descrição curta do dia da semana (valores de "Dom" a "Sáb");
- tem\_str\_dia\_semana_descricao: Descrição do dia da semana (valores de "Domingo" a "Sábado");
- tem\_num\_dia\_ano: Dia no ano (valores de 1 a 366);
- tem\_str\_dia\_ano: Dia no ano como texto (valores de "001" a "366");
- tem\_num\_semana\_ano: Semana no ano (valores de 1 a 52);
- tem\_str\_semana\_ano: Semana no ano como texto (valores de "01" a "52");
- tem\_num\_mes: Mês do ano (valores de 1 a 12);
- tem\_str\_mes: Mês do ano como texto (valores de "01" a "12");
- tem\_str\_mes_sigla: Sigla do mês do ano (valores de "Jan" a "Dez");
- tem\_str\_mes_descricao: Descrição do mês do ano (valores de "Janeiro" a "Dezembro");
- tem\_num\_competencia: Competência (valores como 190001, 202001, 202412, 202501 etc.)
- tem\_str\_competencia: Competência como texto (valores como "01/1900", "01/2020", "12/2024", "01/2025" etc.)
- tem\_str\_competencia1: Competência como texto em outro formato (valores como "Jan/1900", "Jan-2020", "Dez/2024", "Jan/2025" etc.)
- tem_str_competencia2: Competência como texto em outro formato (valores como "1900-01", "2020-01", "2024-12", "2025-01" etc.)
- tem\_num\_bimestre: Bimestre do ano (valores de 1 a 6);
- tem\_str\_bimestre: Bimestre do ano como texto (valores "Jan-Fev", "Mar-Abr", "Mai-Jun", "Jul-Ago", "Set-Out", "Nov-Dez");
- tem\_num\_trimestre: Trimestre do ano (valores de 1 a 4);
- tem\_str\_trimestre: Bimestre do ano como texto (valores "Jan-Mar", "Abr-Jun", "Jul-Set", "Out-Dez");
- tem\_num\_quadrimestre: Quadrimestre do ano (valores de 1 a 3);
- tem\_str\_quadrimestre: Quadrimestre do ano como texto (valores "Jan-Abr", "Mai-Ago", "Set-Dez");
- tem\_num\_semestre: Semestre do ano (valores de 1 a 2);
- tem\_str\_semestre: Semestre do ano como texto (valores "Jan-Jun", "Jul-Dez");
- tem\_num\_ano: Ano (valores de 1899 a 2099);
- tem\_str\_ano: Ano como texto (valores de "1899" a "2099");
- tem_num_quinquenio: Período de 5 anos (valores de 1895, 1900, 1905 a 2095);
- tem_str_quinquenio: Período de 5 anos como texto (valores como "1895-1899", "1900-1905", ..., "2020-2024", "2025-2029", ..., "2095-2099");
- tem\_num\_decada: Década (valores de 1890 a 2090);
- tem\_str\_decada: Década como texto (valores de "1890-1899", "1900-1909", "2010-2019", "2020-2029", ... , "2090-2099");
- tem\_str\_primeiro\_dia\_competencia: Indica se a data é primeiro dia da competência;
- tem\_str\_ultimo\_dia\_competencia: Indica se a data é último dia da competência;
- tem\_str\_primeiro\_dia\_bimestre: Indica se a data é primeiro dia do bimestre;
- tem\_str\_ultimo\_dia\_bimestre: Indica se a data é último dia do bimestre;
- tem\_str\_primeiro\_dia\_trimestre: Indica se a data é primeiro dia do trimestre;
- tem\_str\_ultimo\_dia\_trimestre: Indica se a data é último dia do trimestre;
- tem\_str\_primeiro\_dia\_quadrimestre: Indica se a data é primeiro dia do quadrimestre;
- tem\_str\_ultimo\_dia\_quadrimestre: Indica se a data é último dia do quadrimestre;
- tem\_str\_primeiro\_dia\_semestre: Indica se a data é primeiro dia do semestre;
- tem\_str\_ultimo\_dia\_semestre: Indica se a data é último dia do semestre;
- tem\_str\_primeiro\_dia\_ano: Indica se a data é primeiro dia do ano;
- tem\_str\_ultimo\_dia\_ano: Indica se a data é último dia do ano.

Como pode ser visto na figura, o resultado do processo está direcionado para um arquivo (008. Text file output), mas também pode ser facilmente direcionada a um banco de dados (Table output).

O arquivo ["dim_tem_tempo.csv"](dim_tem_tempo.csv) é uma amostra do resultado total do processo mostrando apenas os seguintes intervalos de datas:
- 30/12/1899 a 31/12/1901;
- 01/01/2024 a 31/12/2025;
- 01/01/2098 a 31/12/2099.

