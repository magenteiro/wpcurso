
# WP Curso
## Desenvolvimento WP do jeito certo
### Este projeto é parte do curso [📚 WP Avançado: Estratégias de Gestão e Desenvolvimento para Freelancers e Agências](https://magenteiro.com/wpavancado/).

## Como usar
* Copie este arquivo para a raiz do projeto que deseja trabalhar a fim de instruir futuros desenvolvedores.
* Siga os passos abaixo para configurar o ambiente de desenvolvimento.


# Definições de projeto
- **Nome do projeto**: WP Curso
- **Cliente**: Magenteiro
- **Versão do PHP**: 8.3
- **Versão do WP**: 6.5


# Configuração do ambiente de desenvolvimento
1. Clone o repositório do templace: `git clone git@github.com:magenteiro/wpcurso.git -b wpadv/templates/docker WPDOCKER`. Isto criará uma pasta WPDOCKER com o conteúdo deste repositório, onde então poderá adicionar um ou mais projetos WordPress.
2. Acesse a pasta do projeto: `cd WPDOCKER`
3. Clone o projeto ou site WordPress/WooCommerce dentro da pasta `wordpress` ou da pasta desejada e mapeada em docker-compose.yml (em wordpress > volumes): `git clone <seuSiteWordpress.git> wordpress`
4. Inicie o ambiente de desenvolvimento: `docker-compose up -d`
5. Adicione o domínio `wordpress.test` (ou outro desejado) ao arquivo hosts do seu sistema operacional apontando para o IP local. Ex: `0.0.0.0    wordpress.test`

**Neste momento você pode importar o banco de dados do projeto ou baixar e instalar uma versão limpa do wordpress.**

### Importando um banco existente
Faça `docker-compose exec -T db mysql -uroot -proot -D wordpress < BANCO.sql` substituindo o nome do arquivo do banco de dados.

### Baixando e instalando uma versão limpa do WordPress
1. Baixe o WordPress na versão especificada: `docker-compose exec wordpress wp core download --version=6.5 --locale=pt_BR --force --allow-root`
2. Instale o WordPress: `docker-compose exec wordpress wp core install --url=https://wordpress.test --title="WP Curso" --admin_user=admin --admin_password=admin --admin_email=seu@email.com --skip-email --allow-root`

# Trabalhando em mais de um projeto WordPress ou WooCommerce
Para trabalhar em mais de um projeto, basta clonar o repositório de um novo projeto em uma nova pasta, e alterar o volume ./wordpress para a nova pasta em docker-compose.yml (em wordpress > volumes).

Por exemplo:
```bash
git clone <outroprojeto.git> outroprojeto
```
E em docker-compose.yml:
```yaml
volumes:
  - ./outroprojeto:/var/www/html
```