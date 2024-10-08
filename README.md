
# 009 Django 5 - Static Files: Bootstrap5 via CDN

Neste repositório, o Boostrap é adicionado via CDN que é uma rede de entrega de conteúdo através da internet. 

Na sequência, no [próximo repositório desta série](https://github.com/Django-Dev-Br/010-Django-4-Static-Files-Bootstrap5-local). Iremos baixar o boostrat via download, seguindo uma boa prática de desenvolvimento para acessá-lo localmente ao invés da internet.

### O que é Bootstrap?

Bootstrap é um dos frameworks front-end mais populares do mundo, projetado para facilitar a criação de sites responsivos e com foco em dispositivos móveis. Criado originalmente pelo Twitter, Bootstrap fornece uma coleção de ferramentas CSS e JavaScript que ajudam os desenvolvedores a construir interfaces de usuário consistentes e atraentes rapidamente. Com Bootstrap, é possível adicionar componentes como botões, formulários, menus de navegação e muito mais, utilizando classes pré-definidas que seguem as melhores práticas de design responsivo. Além disso, o Bootstrap é facilmente integrável com outros frameworks e bibliotecas, tornando-se uma escolha popular para desenvolvedores de todos os níveis.

Documentação oficial: [https://getbootstrap.com/docs/5.3/getting-started/introduction/](https://getbootstrap.com/docs/5.3/getting-started/introduction/)

Melhor tutorial: [https://www.w3schools.com/bootstrap5/](https://www.w3schools.com/bootstrap5/)


## COMO RODAR ESSE PROJETO EM SEU COMPUTADOR:

### Requisitos

- **Python 3.12 com PIP e venv**
- **o Django 5 requer Python 3.10 ou superior.**

- **No [repositório 001](https://github.com/Django-Dev-Br/001-django5-basic-project) há explicações sobre PIP e venv**
  
  [Baixar Python 3.12](https://www.python.org/downloads/release/python-3122/)

   Confira o vídeo para saber como trabalhar com múltiplas versões do Python e com venv (ambiente virtual):
  [![Watch the video](https://img.youtube.com/vi/eetDeQrv0Rs/0.jpg)](https://youtu.be/eetDeQrv0Rs)


### 7 passos simples para executar

1. **Clone o repositório**:
    ```bash
    git clone https://github.com/Django-Dev-Br/009-Django5-static-files-Bootstrap5-CDN.git
    ```

2. **Crie um ambiente virtual**:
   
    **Windows**
    ```bash
     python -m venv myvenv  
    ```
   **Linux**
    ```bash
     python3 -m venv myvenv  
    ```

3. **Ative o ambiente virtual criado**:
   
    **Windows**
    ```bash
    myvenv\Scripts\activate  
    ```

   **Linux**
    ```bash
    source myvenv/bin/activate  
    ```
    
4. **Acesse a pasta do repositório**:
    ```bash
    cd 009-Django5-static-files-Bootstrap5-CDN
    ```
    
5. **Instale o Django**:

   Fazer a instalação após a ativação da virtual env fará com que a instalação seja feita nessa pasta ao invés do computador. Isso significa que o pacote Django não estará disponivel para todos os usuários do computador, mas apenas para o contexto no qual essa venv esteja ativada. Veremos sua ativação logo abaixo.

    **Instalação manualmente via gerenciador de dependências PIP**
    ```bash
    pip install django
    ```
    - use, preferencialmente, a versão 5.1. Para tanto, execute o comando:

     ```bash
    pip install  "django>=5.1,<=5.2"
    ```

    ----- **OU** -----

    **Instalação via arquivo requirements**
    ```bash
    pip install -r requirements.txt
    ```
    O arquivo requirements.txt é um arquivo de texto que contém uma lista de pacotes a ser instalado em uma venv. É uma boa prática de programação do ecossistema Python.

6. **Execute o servidor de desenvolvimento**:
    ```bash
    python manage.py runserver
    ```

7. **Acesse a aplicação no seu navegador**:

   Vá para [http://127.0.0.1:8000/](http://127.0.0.1:8000/) e você verá a imagem `pythondjango.jpg` sendo exibida na página inicial. Compare com o design do [repositório 008](https://github.com/Django-Dev-Br/008-Django5-static-files)

### Código HTML 

Aqui está o código HTML usado para adicionar o Boostrap 5.3.3 ao projeto:

```
 
{% load static %} <!-- Carrega a tag 'static' para uso nos caminhos dos arquivos estáticos -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">  <!-- Adiciona a meta tag para responsividade -->

    <title>Página Inicial</title>
    
    <!-- Latest compiled and minified CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Latest compiled JavaScript -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>

</head>

<body>

    <div class="container">  <!-- Usa um container Bootstrap para centralizar o conteúdo -->

        <h1 class="p-2 m-2">Imagem do Python Django</h1>

        <img class="img-thumbnail"  
             src="{% static 'myapp/images/pythondjango.jpg' %}" 
             alt="Python Django"
             width="60%">
    </div>
    
</body>
</html>
```

### Estrutura de Diretórios do Projeto

```
009-Django5-static-files-Bootstrap5-CDN/
├── manage.py
├── myapp/
│   ├── __init__.py
│   ├── apps.py
│   ├── views.py           # Contém a função 'index' para renderizar 'index.html'
│   └── templates/
│       └── index.html     # Página HTML com Bootstrap 5 via CDN
├── myproject/
│   ├── __init__.py
│   ├── asgi.py
│   ├── settings.py        # Configurações de STATIC_DIRS, STATICFILES_DIRS, STATIC_ROOT
│   ├── urls.py            # URL principal direcionando para 'myapp.views.index'
│   └── wsgi.py
└── static/
    └── myapp/
        └── images/
            └── pythondjango.jpg  # Imagem a ser exibida
└── requirements.txt    # Lista de pacotes Python necessários para o projeto
```

### OBS: Coletando Arquivos Estáticos para Produção

Quando estiver pronto para implantar seu projeto Django em produção, é necessário coletar todos os arquivos estáticos em um único diretório definido por `STATIC_ROOT`. Isso permite que o servidor web sirva esses arquivos de forma eficiente. Para coletar todos os arquivos estáticos, use o comando:

```bash
python manage.py collectstatic
```

Este comando irá procurar todos os arquivos estáticos nos diretórios especificados em `STATICFILES_DIRS` e nas pastas `static/` de cada aplicativo, e copiá-los para o diretório definido por `STATIC_ROOT`.

### Sobre Nosso Treinamento Prático-Profissional com projeto real para iniciantes e avançados em web DevOps Full-stack com Python, Django, Bootstrap e Linux.

[Django Developers Brasil - Aprenda programando enquanto programa aprendendo!](https://django.dev.br/)

Nosso treinamento oferece uma experiência prática de aprendizado de programação, adequada tanto para iniciantes quanto para desenvolvedores avançados. Você participará de um projeto real de desenvolvimento de software em um ambiente corporativo autêntico, onde pessoas com diferentes níveis de conhecimento irão colaborar, aprendendo umas com as outras.

**Junte-se a nós!** E desenvolva as habilidades necessárias para o mercado de trabalho, aprimorando tanto seus conhecimentos técnicos quanto suas soft skills em um ambiente colaborativo e realista.
