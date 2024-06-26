# Simulador Fundeb - Limpeza dos de 2023

O simulador do fundeb utiliza dados de diferentes anos para realizar as simulações. Os dados estão dispersos em diferentes arquivos do Fundeb e é necessário agrupa-los e organiza-los da forma adequada para serem consumidos pelo simulador. Esse projeto limpa os dados obtidos de 2023 para deixa-los adequado a formatação utilizada no simulador.

A principal fonte de dados utilizada foi a [portaria interministerial número 7 de 2023](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/legislacao/2023/portaria-interm-no-7-de-29-12-2023.pdf). Além disso, os resultados obtidos na portaria inteministeria número 7 de 2023 são considerados como resultados de referência do ano de 2023, ou seja, usa-se eles para verificar se os resultados da simulação do cenário base de 2023 estã corretos.

## Projeto

O projeto de limpeza dos do fundeb de 2023. O projeto consiste das seguintes etapas:

1. Obtenção dos dados (extração manual do portal);
2. Conversão dos dados pdf em .xlsx (usando script em python e o portal [ilovepdf](https://www.ilovepdf.com/pt);
3. Limpeza inicial dos dados;
4. Agregação dos dados no formato adequado ao consumo pelo simulador;
5. Simulação para 2024 com os valores padrão;
6. Teste da adequação da simulação de 2024 com a simulação de referência.

## Produto

As seguintes tabelas são esperadas desse projeto:
* Dados de alunos para 2023 por etapa e ente federado;
* Dados de peso por etapa e modalidade de complementação (VAAF e VAAT);
* Dados complementares dos entes federados (recursos, habilitação para etapa VAAT e peso VAAR).


## Scripts

* R:
  * avaliacao_simulacao: testa os resultados da simulação em relação aos resultados obtidos pelo INEP;
  * gera_estrutura_pesos: gera uma tabela em excel para se escrever os pesos manualmente;
  * gera_simulação: 
  * limpa_dados_complementares: obtem dados limpos por scripts intermediários e pela extração dos dados de pdf e os une em uma tabela com os dados complementares que serão usados na simulação;
  * limpa_dados_alunos: limpa dados de alunos agregados pelo script python;
  * limpa_dados_inabilitados: limpa dados de inabilitados para a etapa VAAT;
  * limpa_dados_vaaf: limpa dados de recursos da etapa VAAF;
  * limpa_dados_vaar: limpa dados de recursos de pesos da etapa VAAR;
  * limpa_dados_vaat: limpa dados de recursos da etapa VAAT.
* Python:
  * transforma_matriculas.py: lê arquivos em pdf e extrai valores de matrículas desses arquivos para uma única tabela.

## Fontes

Os dados foram obtidos das seguintes fontes:

* Os números de alunos foram obtidos dos anexos por Unidade da Federação da [portaria interministerial número 7 de 2023](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/matriculas-da-educacao-basica/2023-com-base-na-portaria-interministerial-no-7-de-29-12-2023)
* Os valores de financiamento foram obtidos no [portal do FNDE](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/2023): 
  * Os recursos considerados para o VAAF foram obtidos no anexo da [portaria interministerial número 7 de 2023](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/vaaf/copy2_of_ReceitaeComplementaoporentefederadoFundeb2023.pdf);
  * Os recursos considerados para o VAAT foram obtidos em:
    * [Tabela com os recursos do STN](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/vaat/ReceitaSTN2021nominalparapublicao.pdf);
    * [Tabela com os recursos de Programas Universais](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/vaat/ProgramasUniversais2021nominalparapublicao.pdf);
  * A correção monetária para cálculo dos recursos considerados no VAAT foi obitdo da [nota técnica SEI nº 42380](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/vaat/NotaTcnicaSTNn42380CorreoMonetriaVAAT.pdf).
* Os entes inabilitados para o VAAT foram obtidos no [comunicado do Fundeb sobre a habilitação dos entes](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/2023-1/COMUNICADOHABILITAOFINALVAAT2023.pdf);
* Os pesos considerados para o VAAR foram obtidos no [portaria interministerial número 7 de 2023](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/AnexoVPortariaInterm.n7de29.12.2023.pdf).
* Os pesos de aluno por etapa foram obtidos da [nota técnica conjunto número 12 de 2022](https://www.gov.br/fnde/pt-br/acesso-a-informacao/acoes-e-programas/financiamento/fundeb/notas-tecnicas/NotaTcnicaConjuntan122022.pdf).

