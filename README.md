
# Non-Stoichiometric Methods for Gibbs Free Energy Minimization

Este projeto implementa a minimização da energia livre de Gibbs utilizando dois métodos diferentes: o método de Lagrange não estequiométrico e o método SQP (Sequential Quadratic Programming). O objetivo é determinar as frações molares de 12 espécies químicas sob condições de equilíbrio químico em um sistema fechado.

## Estrutura do Projeto

### Arquivos
- **`non_stoichiometric_lagrange.py`**: Implementação do método de Lagrange.
- **`non_stoichiometric_sqp.py`**: Implementação do método SQP utilizando a biblioteca CasADi.
- **`README.md`**: Explicação do projeto (este arquivo).

## Descrição

O problema envolve a minimização da energia livre de Gibbs de um sistema químico fechado composto por diferentes espécies (N, O, H, NH, NO, NH2, H2O, O2, N2, H2, OH, NO2). A abordagem não estequiométrica é usada para encontrar as frações molares de equilíbrio de cada espécie.

Os métodos implementados neste projeto:
1. **Método de Lagrange (Scipy)**: Resolve o problema utilizando multiplicadores de Lagrange para aplicar as restrições de balanço atômico.
2. **Método SQP (CasADi)**: Usa programação quadrática sequencial para otimizar o problema e encontrar as frações molares.

### Constantes

- **Constante dos gases universais (R)**: 8.314 J/(mol*K)
- **Temperatura (T)**: 3500 K
- **Pressão (P)**: 51 atm (convertido para Pascal)
- **Pressão de referência (P0)**: 1 atm (em Pascal)

### Restrições

- Balanços atômicos para Nitrogênio (N), Oxigênio (O) e Hidrogênio (H).
- As frações molares devem ser não-negativas (maiores ou iguais a zero).

### Equações

As equações envolvem o uso da energia livre de Gibbs padrão de formação e coeficientes estequiométricos para cada espécie. A função objetivo é minimizar a energia livre de Gibbs com restrições de conservação atômica.

### Métodos

#### 1. **Método de Lagrange**

Este método utiliza a biblioteca `scipy.optimize.root` para resolver um sistema de equações não lineares geradas a partir da minimização da função de Gibbs, sujeita a restrições de balanço atômico. A função `L` é utilizada para representar a função de Gibbs com as restrições de Lagrange.

- **Entradas**: Estimativa inicial dos números de mols e valores iniciais para os multiplicadores de Lagrange.
- **Saídas**: Frações molares das 12 espécies e valores dos multiplicadores de Lagrange.

#### 2. **Método SQP**

Neste método, utilizamos a biblioteca CasADi para resolver o problema de programação quadrática sequencialmente. O problema é formulado como um NLP (Nonlinear Programming Problem), onde definimos as equações de balanço e a função de Gibbs como objetivo.

- **Entradas**: Estimativa inicial dos números de mols.
- **Saídas**: Frações molares das 12 espécies.

## Instalação

### Dependências

As seguintes bibliotecas são necessárias:

- `numpy`
- `scipy`
- `matplotlib`
- `casadi`

Você pode instalá-las com o seguinte comando:

```bash
pip install numpy scipy matplotlib casadi
```

## Execução

Para rodar os scripts, basta executar os arquivos Python. Por exemplo, para rodar o método de Lagrange, use:

```bash
python non_stoichiometric_lagrange.py
```

Para rodar o método SQP, use:

```bash
python non_stoichiometric_sqp.py
```

## Comparação de Métodos

Ambos os métodos fornecem resultados semelhantes em termos de frações molares, porém com diferentes tempos de execução e número de avaliações de função. O método SQP, utilizando CasADi, pode ser mais eficiente em termos de número de iterações, dependendo do problema e da estimativa inicial.

## Autores

Este projeto foi desenvolvido por Clarissa Macedo, como parte de um estudo sobre métodos numéricos aplicados à termodinâmica.

---

Este **README** fornece uma visão geral clara e detalhada do seu trabalho. Caso precise de mais alguma alteração ou ajuste, é só me avisar!
