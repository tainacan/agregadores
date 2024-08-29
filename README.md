# Agregadores de Dados

Este repositório contém a configuração para processos de agregação de dados, permitindo coletar e transformar informações de diferentes fontes. Abaixo estão detalhados os principais elementos de configuração presentes no arquivo `setup.yml`.

## Estrutura do Arquivo `setup.yml`

O arquivo `setup.yml` define os processos de agregação através dos seguintes elementos:

### `configs`

O elemento `configs` é uma lista de objetos que representam os diferentes processos de agregação de dados. Cada objeto dentro desta lista contém as seguintes propriedades:

- **name**: (String) O nome do processo de agregação.
- **file**: (String) O endereço para o arquivo que contém o pipe de transformação, que define como os dados serão processados e integrados.
- **inputs**: (Array de Strings) Uma lista de URLs que apontam para as definições das origens de dados. Essas definições descrevem como os dados serão coletados.

### Exemplo de Configuração

```yaml
configs:
  - name: "brasiliana"
    file: https://raw.githubusercontent.com/tainacan/agregadores/main/brasiliana/config.yml
    inputs: 
      - "https://raw.githubusercontent.com/tainacan/agregadores/main/brasiliana/sources.d/Abolicao.yml"
      - "https://raw.githubusercontent.com/tainacan/agregadores/main/brasiliana/sources.d/Missoes.yml"
  - name: "midiateca"
    file: "https://raw.githubusercontent.com/tainacan/agregadores/main/midiateca/config.yml"
    inputs: 
      - "https://raw.githubusercontent.com/tainacan/agregadores/main/midiateca/sources.d/arquivo_publico.yml"
      - "https://raw.githubusercontent.com/tainacan/agregadores/main/midiateca/sources.d/biblioteca_estadual.yml"
      - "https://raw.githubusercontent.com/tainacan/agregadores/main/midiateca/sources.d/galeria_homero_massena.yml"
      - "https://raw.githubusercontent.com/tainacan/agregadores/main/midiateca/sources.d/museu_artes.yml"
      - "https://raw.githubusercontent.com/tainacan/agregadores/main/midiateca/sources.d/museu_colono.yml"
      - "https://raw.githubusercontent.com/tainacan/agregadores/main/midiateca/sources.d/tve.yml"
