# Arquivos de Coleta de Dados

Cada arquivo YAML presente nessa pasta, tem como finalidade definir a configuração para a coleta de dados de uma fonte específica. Os arquivo serve como uma blueprint para o processo de ingestão de dados em uma pipeline de ETL (Extração, Transformação e Carga). Abaixo, uma descrição detalhada de cada seção do arquivo:
todos os arquivos presente nessa pasta fazem parte de um conjunto maior de configurações. Cada arquivo dentro dessa pasta representa uma fonte de dados diferente que será processada por um ramo específico em um fluxo de trabalho orquestrado pelo Apache Airflow. O Airflow utiliza essas configurações para gerenciar e automatizar a ingestão de dados de diversas fontes em um processo ETL.


## 1. `idsource`
- **Descrição:** Um identificador único para a fonte de dados. Esse identificador pode ser usado em outras partes da pipeline para referenciar essa fonte.

## 2. `url`
- **Descrição:** O endereço da API de onde os dados serão coletados. Esta URL aponta para o endpoint que retorna os itens da coleção.

## 3. `url_parameters`
- **Parâmetros:**
  - `order: DESC`
  - `orderby: date`
  - `exposer: json-flat`
  - `mapper: inbcm-ibram`
- **Descrição:** Estes são parâmetros adicionais enviados com a requisição à URL acima. Eles controlam a ordem dos resultados, o formato da resposta, entre outros aspectos específicos da coleta.

## 4. `pagination`
- **pagination.request:`**
  - `pagesize: 50`
  - `field_pagesize: perpage`
  - `field_page: paged`
  - **Descrição:** Configura como a paginação será tratada ao fazer requisições à API. O tamanho da página é definido como 50 itens por página.

- **pagination.response**
  - `path_to_next_page: pagination.next_page`
  - `path_to_items: items`
  - **Descrição:** Especifica como o sistema deve interpretar a resposta da API para encontrar o próximo conjunto de dados e os itens a serem processados.

## 5. `transform`
- **`rename`**
  - **Descrição:** Define como os campos da resposta da API serão mapeados para os nomes de campo usados internamente na pipeline. Além de renomear os campos, também há a possibilidade de definir um campo específico como o identificador único (`use_as_id: true`).
  
- **`add_fields`**
  - **Descrição:** Campos adicionais que serão inseridos em cada item processado. Esses campos são constantes e servem para categorizar os dados, como `museu`, `colecao`, `cidade` e `uf`.

