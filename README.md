# XRF — Fluorescência de Raios X

A técnica de Fluorescência de Raios X baseia-se na emissão por fluorescência para distinguir elementos com base no comprimento de onda ou na energia da radiação emitida. Dessa forma, é possível identificar e quantificar a proporção de cada elemento em uma amostra. Por ser não destrutiva, pode ser aplicada a amostras em pó, sem a necessidade de um ambiente de vácuo.

Uma radiação energética é direcionada à amostra, removendo elétrons das camadas internas dos átomos e levando-os a estados excitados. Isso permite identificar e analisar os elementos presentes em uma amostra de composição desconhecida, porque o espectro das transições eletrônicas (L→K, M→K, M→L) é característico de cada elemento.

## Objetivo

Este repositório identifica os possíveis elementos de uma amostra desconhecida analisada por Fluorescência de Raios X com dispersão de comprimento de onda (WDS) em vácuo. A partir das medições, determina os possíveis picos e, com isso, seleciona os possíveis elementos presentes na amostra. O resultado indica apenas os picos possíveis — não confirma com certeza quais picos são reais.

## Estrutura

- `XRF Picos/elementos-ondas.txt` — tabela com os comprimentos de onda tabelados de Kα e Kβ por elemento.
- `XRF Picos/*.txt` (Ti-U, KCaSn-Cs, Cl, S, P, Si, Al, Mg, Na, F, O) — varreduras de intensidade por ângulo, com passo de 0,1°.
- `XRF Picos/WRX.ipynb` — notebook que processa os dados e gera os gráficos.

## Como funciona

1. Carrega a tabela de elementos (Kα e Kβ).
2. Converte cada ângulo em comprimento de onda pela lei de Bragg (n = 1), usando o valor de `2d` correspondente ao grupo.
3. Registra os pontos cujo comprimento de onda está próximo (tolerância `atol = 0.04`) de um Kα/Kβ tabelado.
4. Para cada elemento, mantém o candidato de maior intensidade e confirma como pico os máximos locais.
5. Salva os picos de cada grupo e plota a curva de intensidade com os picos marcados.
