# DeepFake Shakespeare

## 🧑‍💻 ALUNOS:
- ALEXANDER NUNES SOUZA
- ISAAC LEVI LIRA DE OLIVEIRA
- LAILA MARIA ALVES SANTOS
- MATHEUS VINICIUS RAMOS
- PERICLES MAIKON DE JESUS COSTA

## 📜 Visão Geral
DeepFake Shakespeare é um gerador de textos literários que usa inteligência artificial para criar obras no estilo do dramaturgo William Shakespeare. O sistema emprega modelos de linguagem avançados com fine-tuning dedicado para capturar os elementos linguísticos, estruturais e estilísticos característicos das obras do bardo inglês, criando peças, monólogos e cenas que Shakespeare nunca escreveu, mas que poderiam ter existido.

## ✨ Recursos Principais
Geração de Texto Shakespeariano: Crie cenas, monólogos no estilo autêntico de Shakespeare
Análise de Autenticidade: Avaliação detalhada da qualidade "shakespeariana" do texto gerado
Visualização de Cenas: Geração de imagens que representam visualmente as cenas criadas
Personalização: Defina temas, número de personagens e tipo de texto desejado

## 🔧 Detalhes Técnicos
### Modelos e Fine-tuning
O projeto utiliza modelos de linguagem GPT com fine-tuning especializado em textos shakespearianos. Cinco variantes foram treinadas e comparadas:

1. Modelo 1 (ft:gpt-4o-mini-2024-07-18:hendrik::BJ8DAYRn)
    - 20 exemplos de treinamento
    - 3 épocas
    - Sofreu de overfitting
2. Modelo 2 (ft:gpt-4o-mini-2024-07-18:hendrik::BJ95WQdI)
    - 20 exemplos
    - 1 época, learning rate: 0.1
3. Modelo 3 (ft:gpt-4o-mini-2024-07-18:hendrik::BJa2oeL5)
    - 20 exemplos
    - 1 época, learning rate: 0.1, batch size: 8
4. Modelo 4 (ft:gpt-4o-mini-2024-07-18:hendrik::BJkjPlqi)
    - 50 exemplos
    - 1 época, learning rate: 0.15, batch size: 8
5. Modelo 5 (ft:gpt-4o-mini-2024-07-18:hendrik::BJkuBW58)
    - 100 exemplos
    - 2 épocas, learning rate: 0.2, batch size: 16

### Dataset
O treinamento utilizou o dataset "Shakespeare Play's Dialogues" do Kaggle, contendo diálogos autênticos de:

- Hamlet
- Macbeth
- Romeu e Julieta

Os dados foram processados para criar exemplos de treinamento que preservam a estrutura dramática original, incluindo:

- Direções de palco
- Identificação de personagens
- Estrutura de atos e cenas

## 💻 Instalação e Configuração

```
# Clone o repositório
git clone https://github.com/shh4und/llm-shakes.git

# Instale as dependências
pip install install kagglehub[pandas-datasets] gradio openai

# Configure sua chave de API da OpenAI em seu ambiente (exemplo Google Colab):
from google.colab import userdata
key = userdata.get('openAIkey')
from openai import OpenAI
client = OpenAI(api_key=key)
```

### 🚀 Como Usar
Interface Web (Gradio)
```
# Iniciar a aplicação
demo = criar_aplicacao_shakespeare()
demo.launch()
```

Uso Programático no Jupyter Notebook / Colab
```
# Gerar um monólogo sobre a Revolução Industrial
texto = gerar_texto_shakespeare(
    tema="A Revolução Industrial", 
    tipo_texto="monologo", 
    personagens=1,
    temperatura=0.8,
    model="ft:gpt-4o-mini-2024-07-18:hendrik::BJkuBW58"  # Modelo 5
)

# Analisar a qualidade shakespeariana
analise = analisar_estilo_shakespeare(texto)
```
## 📚 Referências
- Dataset: [Shakespeare Play's Dialogues (Kaggle)](https://www.kaggle.com/umerhaddii/shakespeare-plays-dialogues)
- Documentação de Fine-tuning: [OpenAI Documentation](https://platform.openai.com/docs/guides/fine-tuning)
- [The Complete Works of William Shakespeare](shakespeare.mit.edu)
