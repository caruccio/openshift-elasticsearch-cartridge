OpenShift ElasticSearch Cartridge
=================================
Cartridge ElasticSearch para a plataforma Getup Cloud OpenShift.

Para criar sua aplicação ElasticSearch, primeiro vcê precisa registrar-se na Getup.
Acesse http://getupcloud.com/#/sign-up e faça seu cadastro.
Você recebe gratuitamente 750hs para testar a plataforma.

Para criar sua app ElasticSearch, execute no terminal:

    rhc app create <nome do app> http://reflector-getupcloud.getup.io/github/getupcloud/openshift-elasticsearch-cartridge

Se deseja criar um cluster ElasticSearch, inclua a opção `--scaling` ao comando:

    rhc app create <nome do app> http://reflector-getupcloud.getup.io/github/getupcloud/openshift-elasticsearch-cartridge --scaling


Adicionando nodes ao cluster
============================
Para adicionar novos nodes ao cluster, simplesmente adicione gears a sua aplicação:

    rhc cartridge scale -a <nome do app> elasticsearch <número total de gears>


Plugins
=======
Para instalar plugins, edite o arquivo `plugins.txt` e publique as alterações. O arquivo possui alguns exemplos prontos, basta descomentar as linhas desejadas.

    cd elasticsearch
    vim plugins.txt
    git commit -a -m 'Incluindo plugin XXX'
    git push

Você ainda pode instalar plugins a partir de arquivoz zip. Basta colocá-los no diretorio `plugin/`, comitar e publicar.


Configuração
============
As configurações são construidas durante o deploy, iniciando com o conteúdo do arquivo `config/elasticsearch.yml.erb`, concatenado
com os arquivos encontrados em `config` (com exceção de logging.yml e elasticsearch.in.sh). Arquivos com extensão .erb serão
pre-processados usango o comando ruby erb.


Licença
=======
Este projeto é licenciado sob [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.html).
