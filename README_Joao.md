# Sistema Especialista para Diagnóstico Automotivo

Sistema especialista desenvolvido em Python para realizar uma **triagem inicial de problemas automotivos** a partir dos sintomas informados pelo usuário. O sistema utiliza regras de produção e encadeamento para frente (*Forward Chaining*) para relacionar os fatos coletados a possíveis diagnósticos e recomendações.

> **Aviso:** este projeto oferece apoio à triagem. Não substitui a avaliação presencial de um mecânico ou profissional automotivo.

## Objetivo

Auxiliar o usuário na identificação preliminar de possíveis falhas do veículo, apresentando:
- perguntas sobre os sintomas;
- diagnósticos baseados em regras;
- recomendações iniciais;
- registro das regras ativadas e explicação do raciocínio.

## Como funciona

O fluxo principal do sistema é:

1. **Coleta de informações:** pergunta se o motor liga e, conforme a resposta, direciona a investigação.
2. **Validação das respostas:** aceita `S` (sim) ou `N` (não), ignorando espaços extras e diferenças entre maiúsculas e minúsculas.
3. **Armazenamento dos fatos:** registra as respostas em um dicionário, com valores booleanos (`True` ou `False`).
4. **Motor de inferência:** percorre a base de regras e verifica quais condições são satisfeitas pelos fatos.
5. **Geração das conclusões:** cada regra ativada apresenta um diagnóstico e uma recomendação.
6. **Explicação do raciocínio:** exibe as regras acionadas e os fatos que justificaram cada conclusão.
7. **Tratamento de exceções:** informa quando a execução é interrompida ou quando ocorre um erro inesperado.

### Exemplo de regra

A regra `R18` é ativada quando:
- o motor liga;
- há cheiro de queimado;
- existe sinal de vazamento de fluido.

Quando essas condições são verdadeiras, o sistema indica uma situação que exige atenção e recomenda interromper o uso por precaução e realizar uma inspeção imediata.

## Tecnologias e conceitos

- **Python**
- Dicionários e valores booleanos
- Funções e métodos
- Expressões `lambda`
- Estruturas condicionais e de repetição
- Tratamento de exceções (`try/except`)
- Sistema baseado em regras
- Encadeamento para frente (*Forward Chaining*)

## Requisitos

- Python 3 instalado

O código apresentado utiliza apenas recursos da biblioteca padrão do Python, portanto não exige a instalação de dependências externas.

## Como executar

1. Clone o repositório:

   ```bash
   git clone URL_DO_REPOSITORIO
   ```

2. Acesse a pasta do projeto:

   ```bash
   cd NOME_DO_REPOSITORIO
   ```

3. Execute o arquivo principal (substitua pelo nome correto do arquivo):

   ```bash
   python main.py
   ```

   Em alguns ambientes, pode ser necessário usar:

   ```bash
   python3 main.py
   ```

4. Responda às perguntas digitando `S` para sim ou `N` para não.

## Estrutura do projeto

A estrutura pode variar conforme a organização do repositório. Um exemplo:

```text
.
├── main.py              # Arquivo principal do sistema
├── README.md            # Documentação do projeto
└── ...
```

## Limitações

- Os diagnósticos dependem das regras cadastradas e dos sintomas informados.
- O sistema não realiza leitura direta de sensores ou módulos eletrônicos do veículo.
- A recomendação é preliminar e pode não identificar todas as causas possíveis.
- A precisão depende da qualidade e da abrangência da base de regras.

## Contribuição

Para contribuir, crie uma branch, implemente suas alterações, teste o funcionamento e envie um Pull Request.

## Licença

Nenhuma licença foi definida neste momento. Caso o projeto seja disponibilizado publicamente, considere adicionar um arquivo `LICENSE` com a licença escolhida.
