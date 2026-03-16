# Voxel Neural Network Compiler (NN Generator v12.0)

**Nota de Engenharia:** Esta ferramenta é um transpilador especializado que converte modelos de arquitetura de Redes Neurais Artificiais (ANN) em linguagem de script executável nativamente por motores de voxel (Minecraft Commands). O foco principal é a automação da escrita de algoritmos matriciais e a otimização do gradiente descendente em ambientes de execução baseados em scoreboards.

## Visão Geral
O sistema permite a configuração de Redes Neurais Profundas (Deep Learning) com múltiplas camadas ocultas e automatiza a geração de três módulos críticos:
1. **Setup:** Inicialização de memória física (Armor Stands) e alocação de registros (Objectives).
2. **Forward Pass:** Cálculo de inferência assíncrona com funções de ativação.
3. **Backpropagation:** Algoritmo de retropropagação para ajuste de pesos e vieses.

## Engenharia de Software e Algoritmos

### 1. Sistema de Endereçamento Dinâmico (Alpha Tagging)
Diferente de sistemas estáticos, este gerador utiliza um algoritmo de conversão decimal para base alfabética (`getAlphaTag`) para criar identificadores únicos e persistentes para cada neurônio. Isso permite o endereçamento direto de dados entre camadas distintas sem conflitos de memória, funcionando como um sistema de ponteiros lógicos.

### 2. Transpilação de Matemática Matricial
O compilador traduz operações de multiplicação de matrizes (Pesos x Entradas) para uma sequência otimizada de comandos `/scoreboard players operation`. 
* **Gerenciamento de Escopo:** O sistema organiza sufixos de variáveis automaticamente para garantir que cada neurônio acesse apenas os pesos e deltas correspondentes à sua camada de origem e destino.

### 3. Backpropagation "Math Perfection" 
A versão atual foca na correção da **Dupla Penalização** de gradiente.
* **Otimização do Delta:** A derivada da função de ativação ReLU é aplicada estritamente no cálculo do Delta da camada, eliminando redundâncias computacionais durante a atualização dos pesos.
* **Propagação de Erro Cross-Layer:** O script gera a lógica de "Erro Acumulado", onde cada neurônio da camada atual contribui proporcionalmente para o erro da camada anterior, permitindo o treinamento de redes profundas dentro do motor do jogo.

## Funcionalidades Técnicas
* **Abstração de Ponto Flutuante:** Integração automática do sistema de escalonamento (Math Scaling) para simular cálculos decimais em uma engine que suporta apenas inteiros de 32 bits.
* **Automação de Spawning:** Cálculo geométrico de coordenadas X/Y/Z para visualização da topologia da rede no ambiente 3D, facilitando o debugging visual dos pesos e ativações.
* **Interface de Parametrização:** Controle granular de Hyperparameters (Taxa de Aprendizado de Pesos e Biases) via UI, refletindo instantaneamente no código gerado.

---
*Ferramenta desenvolvida para acelerar a prototipagem de sistemas autônomos e experimentação de algoritmos de inteligência artificial em ambientes simulados de alta restrição.*
