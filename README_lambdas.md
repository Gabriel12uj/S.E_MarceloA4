Uso de lambda no SistemaEspecialistaOficina
Neste projeto, lambda é usado para definir a condição lógica de cada regra diretamente dentro da base de conhecimento (_carregar_regras), sem precisar criar várias funções nomeadas com def fora da estrutura da regra.

O que é o lambda aqui?
Em Python, lambda cria uma função anônima (sem nome) de expressão única. Na chave "condicao" de cada regra, ela recebe o dicionário de fatos (f) e avalia se os sintomas informados atendem àquela regra:

Python
{
    "id": "R04",
    "condicao": lambda f: f["motor_liga"] and f["barulho_freio"],
    "fatos_desc": "motor_liga=True, barulho_freio=True",
    "diagnostico": "Possível desgaste no sistema de freios (chiado ou rangido ao frear).",
    "recomendacao": "Inspecionar pastilhas, discos e demais componentes de frenagem.",
}
f: representa self.fatos quando a função é chamada pelo motor de inferência.

and e not: combinam e invertem os valores booleanos (True / False) dos fatos.

Retorno: o lambda retorna apenas True ou False — ele não retorna o texto de "diagnostico" nem de "recomendacao".

Como o motor de inferência usa o retorno do lambda
Na função executar_inferencia(), o sistema percorre as regras e executa regra["condicao"](self.fatos) dentro de um if:

Python
for regra in self.regras:
    if regra["condicao"](self.fatos):
        self._registrar(
            regra["id"],
            regra["fatos_desc"],
            regra["diagnostico"],
            regra["recomendacao"],
        )
regra["condicao"](self.fatos) passa o dicionário de fatos para o lambda.

Se todas as partes exigidas pela condição forem verdadeiras (True), o lambda devolve True.

O if detecta True, dispara a regra e chama _registrar(...), que então lê "diagnostico" e "recomendacao" daquele dicionário e grava o passo no histórico de explicação.

Se o retorno for False, a regra não dispara e o loop segue para a próxima.

Por que usar lambda nesse código?
Organização: cada regra mantém sua condição colada ao seu id, fatos_desc, diagnostico e recomendacao.

Menos código repetitivo: evita escrever mais de vinte funções def separadas apenas para testar combinações booleanas de fatos.
