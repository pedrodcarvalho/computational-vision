### **Comparação entre Lab 7-8 (Primeiro Bloco de Código) e Projeto Final (Segundo Bloco de Código)**

1. **Primeiro Bloco de Código: ResNet para Detecção de Máscaras Faciais**

   - **Problema**: Detecção de máscaras faciais em imagens reais em RGB (classificação multiclasse: `com_máscara`, `sem_máscara`, `máscara_usada_incorretamente`).
   - **Conjunto de Dados**: Imagens reais em RGB com características complexas.
   - **Abordagem**:
     - Aproveita o **ResNet18 pré-treinado**, uma Rede Neural Convolucional (CNN) projetada para classificação de imagens.
     - ResNet é uma arquitetura altamente eficiente com muitas camadas convolucionais e conexões de atalho (skip connections). Ela extrai características espaciais e hierárquicas complexas, ideal para dados de imagem.
     - Não é necessário definir camadas personalizadas, pois o modelo pré-treinado é reaproveitado, alterando apenas a camada totalmente conectada (fully connected) final para classificar em 3 categorias.

2. **Segundo Bloco de Código: Modelo Personalizado para Fashion MNIST**
   - **Problema**: Classificação de dígitos manuscritos (classificação multiclasse: 10 dígitos).
   - **Conjunto de Dados**: Fashion MNIST (imagens em escala de cinza, 28x28 pixels).
   - **Abordagem**:
     - Define uma **rede totalmente conectada (fully connected)** personalizada com 2 camadas ocultas.
     - Adequada para conjuntos de dados simples e de baixa resolução, onde a extração de características com CNN pode ser desnecessária.
     - Utiliza camadas definidas manualmente (`nn.Linear`, `nn.ReLU`, etc.) em vez de modelos pré-treinados mais complexos.

---

### **Diferenças na Arquitetura**

#### **ResNet (Primeiro Bloco de Código)**

- **Propósito**: Projetado para conjuntos de dados de imagens de alta resolução e complexidade. Usa camadas convolucionais para extração de características.
- **Modelo Pré-treinado**:
  - ResNet já foi treinado em grandes conjuntos de dados (ex.: ImageNet), fornecendo capacidades gerais de extração de características.
  - Apenas a última camada de classificação (`fc`) é ajustada para 3 classes.
- **Vantagens**:
  - Evita treinar uma rede profunda do zero (economiza tempo e recursos computacionais).
  - Útil para conjuntos de dados pequenos, já que os pesos pré-treinados atuam como um forte ponto de partida.

#### **Rede Feedforward Personalizada (Segundo Bloco de Código)**

- **Propósito**: Feita sob medida para conjuntos de dados simples e de pequena escala, como o Fashion MNIST.
- **Arquitetura**:
  - Camadas totalmente conectadas (`Linear`) processam as imagens achatadas (flattened).
  - Utiliza `ReLU` para não-linearidade e `Softmax` para saídas de probabilidade.
- **Vantagens**:
  - Computacionalmente leve.
  - Oferece mais flexibilidade para aprender a partir do zero.

---

### **Quando Usar Cada Abordagem**

- **Primeiro Bloco de Código**:

  - Ideal para tarefas que envolvem imagens reais e complexas.
  - Útil quando modelos pré-treinados podem reduzir o esforço de projetar e treinar do zero.
  - Perfeito para cenários de aprendizado por transferência (transfer learning) e fine-tuning.

- **Segundo Bloco de Código**:
  - Funciona bem para conjuntos de dados de baixa resolução e em escala de cinza, onde arquiteturas feitas à mão são suficientes.
  - Adequado para fins educacionais ou para explorar o design de modelos personalizados.
  - Permite um entendimento detalhado da arquitetura e do treinamento do modelo.

---

### **Conclusões**

- A primeira abordagem utiliza uma estratégia de **aprendizado por transferência**, aproveitando uma CNN pré-treinada sofisticada para uma tarefa desafiadora.
- A segunda abordagem define uma arquitetura personalizada e mais simples para um conjunto de dados mais direto.
- A escolha entre essas abordagens depende de:
  - Complexidade do conjunto de dados e da tarefa.
  - Recursos computacionais disponíveis.
  - Necessidade de aprendizado por transferência versus criação de um modelo do zero.
