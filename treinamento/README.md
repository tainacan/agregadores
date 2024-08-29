# [config.yml] Configuração de Transformação de Dados

Este arquivo YAML define o processo de transformação de dados utilizado no pipeline de agregação. O objetivo é processar, transformar e mapear os dados coletados para uma coleção-alvo. Abaixo está a explicação detalhada de cada seção do arquivo.

## Estrutura do Arquivo

### `pipe`

A seção `pipe` é a seção principal do arquivo ela define e agrupa as transformações a serem aplicadas e o mapeamento a ser utilizado para a coleção de destino.

#### `path_root`

- **Descrição**: Define o caminho raiz dos dados que serão processados no pipeline, essa configuração é requirida para padronizar a ingestão de dados oriunda das fontes de dados definidas na propriedade "inputs" do arquivo: https://github.com/tainacan/agregadores/blob/main/treinamento.yml.
- **exemplo**: `"payload"`

#### `transform`

A subseção `transform` especifica as operações de transformação que serão aplicadas aos dados.

##### `strip`

- **Descrição**: Remove os campos especificados dos dados.

##### `lowercase`

- **Descrição**: Converte os valores dos campos especificados para minúsculas.

##### `split`

- **Descrição**: Divide os valores dos campos especificados com base em um delimitador.

##### `capitalize`

- **Descrição**: Converte a primeira letra de cada palavra do campo especificado para maiúscula.


##### `add_hash`

- **Descrição**: Gera hash baseado em combinações de campos especificados e armazena nos campos de destino.


### `target_collection`

A seção `target_collection` define a configuração para a coleção de destino onde os dados transformados serão armazenados.

#### `connection_name`

- **Descrição**: O "Connection Id" da conexão do Airflow (/connection/list/) utilizada para acessar a coleção de destino.
Devem está devidamente configurada com os dados de "Host", "Login", "Password" "Connection Type=http"
- **Valor**: `"treinamento.local"`

#### `collection_id`

- **Descrição**: O identificador da coleção de destino.
- **Valor**: `"5"`

#### `metadata_identifier`

- **Descrição**: O metadado que guarda o identificador único dos itens no processo de agregação.

#### `metadata_hash_content`

- **Descrição**: O metadado utilizado para armazenar o hash do conteúdo do item.

#### `ignore_items_without_identifier`

- **Descrição**: Configuração que, quando definida como `true`, faz com que itens sem identificador sejam ignorados.

#### `metadata`

- **Descrição**: Mapeamento dos metadados da origem para os metadados da coleção de destino.
- **exemplo**:
  - `"37"`: `"id"`
  - `"7"`: `"resumo-descritivo"`
  - `"8"`: `"titulo"`
  - `"32"`: `"numero-registro"`
  - `"29"`: `"situacao"`
  - `"28"`: `"autor"`
  - `"26"`: `"classificacao"`
  - `"33"`: `"museu"`
  - `"35"`: `"fingerprint"`
  - `"36"`: `"url"`
  - `"32221"`: `"colecao"`
  - `"32413"`: `"cidade"`
  - `"32417"`: `"uf"`
  - `"4991391"`: `"hash-content"`
  - `"_thumbnail"`: `"thumbnail"`
  - `"_document"`: `"document"`
