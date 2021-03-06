# Corpus do Português e Modelos Diversos

Esse projeto foi criado para dar facilidade no acesso a um Corpus do Português que tenha uma quantidade de palavras e sentenças relevantes. Mesmo com projetos em algumas universidades o acesso não é facilitado e alguns corpus exigem pagamento. 

Primeiramente será criado um Corpus do Português/BR através de um dump do Wikipedia: https://dumps.wikimedia.org

Após será gerado um modelo usando o wordrep da library MITIE: https://github.com/mit-nlp/MITIE/tree/master/tools/wordrep

Serão disponibilizados todas as ferramentas que serão utilizadas, bem como o resultado, como para gerar o modelo do MITIE exige muito processamento e memória é algo que realmente pode ajudar quem precisa de um modelo.

Ajudas bem-vindas:

* Corpus diversos do Português;
* Modelos prontos; 

## Convertendo um dump Wikipedia para somente texto

O pré-processamento do dump do Wikipedia é feita por uma ótima ferramenta, extremamente performática e licenciada sob a licença MIT. Ela é desenvolvida em uma linguagem não muito comum, a Nim, mas ela gera binários para várias plataformas. Mais detalhes pode ser encontrados no repositório do Nim: https://github.com/rspeer/wiki2text

Por padrão o wiki2text inclui o header de cada artigo no formato: == [titulo] == , é necessário remover com grep -v para ficar um corpus mais limpo. O comando para a extração do texto é semelhante a:

``` bunzip2 -c dump_wikipedia_compactado.xml.bz2 | ./wiki2text | grep -v '^=' > ptwiki.txt ```

## Mais do que artigos

Caso deseje um corpus com linguagem mais informal, é só incluir também os metadados do Wikipedia, pois isso inclui as discussões nos artigos, que é geralmente feita por mensagens mais informais entre os membros do Wikipedia. Geralmente quanto mais polêmico o artigo é, mais discussão e mais informalidade, veja um exemplo na seguinte página: https://pt.wikipedia.org/wiki/Discussão:Inri_Cristo

## Downloads

### Corpus

Como os corpus são muito grandes não é possível incluir no Github, estão disponíveis para download através dos links:

| Corpus            | Qtde Palavras | Link                                                          |        Versão |
|-------------------|---------------|---------------------------------------------------------------|---------------|
| Artigos Wikipedia + Corpus Laps UFPA | 270.139.795 | https://s3-us-west-2.amazonaws.com/datamodelpublic/models/pt_wiki_270_139_795_v1_0_1.rar | 1.0.1 |
| Artigos Wikipedia | 244.188.490   | https://s3-us-west-2.amazonaws.com/datamodelpublic/models/pt_wiki_244_188_490.zip | 1.0

Se quiser remover as pontuações do corpus basta usar o seguinte comando no bash:

cat input_file | tr -d '[:punct:]' > output_file

Exemplo: 

cat pt_wiki_corpus.txt | tr -d '[:punct:]' > pt_wiki_corpus_without_punct.txt

### Modelos

| Modelo            | Tipo          | Link                                                          |
|-------------------|---------------|---------------------------------------------------------------|
| Mitie NLP         | total_word_feature_extractor   | https://s3-us-west-2.amazonaws.com/datamodelpublic/models/modelos/total_word_feature_extractor.zip |
| Mitie NLP         | top_words   | https://s3-us-west-2.amazonaws.com/datamodelpublic/models/modelos/top_words.zip|
| Mitie NLP         | word_vects   | https://s3-us-west-2.amazonaws.com/datamodelpublic/models/modelos/word_vects.zip |



## Licença dos dumps Wikipedia e os corpus gerados

A linceça dos dumps e dos corpus gerados a partir do Wikipedia seguem o licenciamento do Wikipedia, disponível em https://dumps.wikimedia.org/legal.html

## Chatbot

Estou desenvolvendo um motor de um chatbot utilizando o Corpus, caso queiram maiores informações, favor enviar um email.


