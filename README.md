# Analisando Textos com o Language Studio

A proposta deste repositório é trazer um tutorial passo a passo para exemplificar a análise de textos com o Language Studio.

A iniciativa da criação deste repositório foi para registrar a resolução do exercício 'Processamento de Linguagem Natural' que é parte do curso [Microsoft Azure AI Fundamentals](https://web.dio.me/track/microsoft-azure-ai-fundamentals) fornecido pela Digital Innovation One - [DIO](https://www.dio.me/), este em preparação para a certificação AI-900: Microsoft Azure AI Fundamentals.

Espero poder ajudar todos aqueles que por ventura vierem a este repositório.


## Apresentação dos Problemas

O problema que iremos resolver é o mesmo apresentando pela Microsoft Learn com o título 'Analyze text with Language Studio', este problema pode ser encontrado [aqui](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/06-text-analysis.html).

O problema proposto é o seguinte:

> "Neste exercício, você explorará os recursos da linguagem Azure AI analisando alguns exemplos de avaliações de hotéis. Você usará o Language Studio para entender se as avaliações são em sua maioria positivas ou negativas.

> Por exemplo, suponha que a agência de viagens fictícia Margie’s Travel incentive os clientes a enviar avaliações sobre estadias em hotéis. Você pode usar o serviço de idiomas para identificar frases-chave, determinar quais avaliações são positivas e quais são negativas ou analisar o texto da avaliação em busca de menções a entidades conhecidas, como locais ou pessoas."

## Pré-requisitos para resolução do problema

* Ter uma conta do Microsoft Azure. (Caso você não tenha um conta será necessário criar, para isto siga os passos que serão apresentados abaixo)

* Ter muita vontade e disposição para aprender.


#### Passo a Passo para criar a conta no Microsoft Azure

* Acesse o site da [Microsoft Azure](https://azure.microsoft.com/pt-br/free/search/?ef_id=_k_CjwKCAiA_aGuBhACEiwAly57MQIxpbuFTl1YFmHB1o36Rq5fAlKA8JO9CdOLPuyq_oV_3JBza8E_-hoC4OAQAvD_BwE_k_&OCID=AIDcmmzmnb0182_SEM__k_CjwKCAiA_aGuBhACEiwAly57MQIxpbuFTl1YFmHB1o36Rq5fAlKA8JO9CdOLPuyq_oV_3JBza8E_-hoC4OAQAvD_BwE_k_&gad_source=1&gclid=CjwKCAiA_aGuBhACEiwAly57MQIxpbuFTl1YFmHB1o36Rq5fAlKA8JO9CdOLPuyq_oV_3JBza8E_-hoC4OAQAvD_BwE)
* Clique em Experimente gratuitamente ou no botão Início gratuito.
* Será necessário colocar os dados de sua conta da Microsoft, que em geral é de um e-mail da hotmail ou outlook.
* Siga os passos conforme solicitado.

**OBS**: Será necessário cadastrar um cartão de crédito para aderir ao plano gratuito, inicialmente você terá $200 dólares de crédito ou 30 dias para testar os serviços, prevalecendo o que acabar primeiro.

## Passo a Passo para resolver o problema

Agora que você já tem uma conta da Microsoft Azure, vamos começar:

1. Acesse o [Portal da Azure](https://portal.azure.com/) para começar a resolver o problema.

2. Na aba Azure Services procure por 'Create a Resource'.

![Create a Resource](https://i.ibb.co/XXZsckw/Create-a-Resource.png)

3. Em seguida pesquise por Language Service. 

![Language Service](https://i.ibb.co/23BDrX8/Language-Service.png)

4. Após acessar o Language Service, clique no botão 'create' e depois em Continue to create your resource. 

![Create Language Service](https://i.ibb.co/mGk29tz/Create-Language-Service.png)

5. Neste página você irá criar um Language Service Workspace. Com os seguintes dados:
 

    Subscription: Aqui é a sua inscrição do Microsoft Azure, se você estiver com uma conta gratuita, provavelmente apareça ela como padrão.

    Resource group: Criar ou selecionar um Grupo de Recursos. (Como provavelmente você não terá um Grupo de Recursos para selecionar, deverá criar um clicando no botão create new, então deverá colocar um nome para o mesmo e clicar em ok. Experimente colocar **LanguageServiceRG**, onde LanguageService é referente ao servico e RG é Resource Group)

    Region: Sugiro você colocar a região East US. Que é a mais próximo com custo mais baixo.
    
    Name: Entrar com um nome único para seu Workspace. Neste caso aqui sugiro colocar **lab-languageservice**, mas pode ser qualquer nome a sua escolha.

    Pricing tier: Selecione Free F0 (5K Trasactions per 30 days)

    Marque a caixa By checking this box I cert....

5. Após o preenchimento dos dados iremos clicar no botão azul 'Review + Create'. 

![Review + Create](https://i.ibb.co/Jv69sQR/Review-create.png)

6. Clique no botão Create. Após clicar no botão Create, espere o Deployment finalizar. Aparecerá a mensagem 'Your deployment is complete'.

![Validation Passed e Create](https://i.ibb.co/6tqdQLN/Create-language.png
)

7. Após a o deploy está completo, iremos acessar a página do Language Service, para isso [clique aqui](https://language.cognitive.azure.com/). Após o acesso a pagina, provavelmente será necessário fazer o login.  

8. Assim que você acessar/fazer login irá aparecer uma caixa de diálogo para selecionar o recurso do Azure. Você deverá prencher com as seguintes informações e clicar em Done.

    Azure directory: Diretório Padrão
    
    Subscription: Aqui é a sua inscrição do Microsoft Azure, se você estiver com uma conta gratuita, provavelmente apareça ela como padrão, senão selecione 'Azure subscription 1'.

    Resource type: Language.
    
    Resource name: O recurso que criamos nos passos atrás, de nome **lab-languageservice**.


![Recurso do Azure](https://i.ibb.co/gFqyxyq/Recurso-do-Azure.png)

9. Agora na aba Classify text iremos selecionar o serviço 'Analyze sentiment and mine opinions'.

![Analyze sentiment](https://i.ibb.co/wR1zjG8/Analyze-sentiment-and-mine-opinions.png)

10. Na próxima tela iremos selecionar o idioma English e o Azure resource o **lab-languageservice**, provavelmente eles já virão como padrão. Para analisar os comentários dos clientes sobre o hotel, poremos copiar e colocar na caixa de texto ou então fazer o upload de um arquivo txt com todos os comentários. Que é o que iremos fazer neste exemplo. Clique em Browse for a file e selecione o arquivo em questão. Você poderá baixar o arquivo teste na pasta input deste repositório. Após selecionar o texto presente no arquivo txt será automaticamente transcrito na caixa de texto.

![Texto para análise](https://i.ibb.co/HGJMhxv/Texto-para-analise.png)

11. Marque a caixa I acknowledge that runn... e em seguida clique em run.

![Marque a caixainha e run](https://i.ibb.co/T2zJ0RR/Marque-caixinha-e-run.png)

12. Pronto agora é só analisar as reviews e sentimentos dos clientes sobre o hotel.

![MResultado sentimentos](https://i.ibb.co/hm6j1Xs/Resultado-sentimentos.png)

Parabéns! Você fez todo o processo!



## Meus Contatos

[![LinkedIn](https://img.shields.io/badge/LinkedIn-000?style=for-the-badge&logo=linkedin&logoColor=0E76A8)](https://www.linkedin.com/in/tiagolisboanovais/)

[![Instagram](https://img.shields.io/badge/instagram-000?style=for-the-badge&logo=instagram&logoColor=0E76A8)](https://www.instagram.com/tiagolisboa.ti/)

[![E-mail](https://img.shields.io/badge/-Email-000?style=for-the-badge&logo=microsoft-outlook&logoColor=007BFF)](mailto:tiagolisboanovais)

[![Github](https://img.shields.io/badge/github-000?style=for-the-badge&logo=github&logoColor=0E76A8)](https://github.com/tiagolisboanovais)
