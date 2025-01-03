# Anotações do Curso

### Dockerfile: O coração da imagem
O Dockerfile é um arquivo de texto com instruções para construir uma imagem. Cada instrução cria uma nova camada na imagem.

### Principais instruções do Dockerfile

##### FROM (Imagem base)
Define a imagem base para construir a nova imagem.
Exemplo:

```dockerfile
FROM ubuntu:20.04
```
- Você pode usar imagens mínimas como alpine para reduzir o tamanho.

##### RUN (Executa comandos durante a construção)
Usada para instalar pacotes ou configurar o ambiente.
Exemplo:

```dockerfile
RUN apt-get update && apt-get install -y python3
```

##### COPY e ADD (Adicionam arquivos à imagem)
- **COPY**: Copia arquivos ou diretórios locais para a imagem.

```dockerfile
COPY app.py /app/
```

- **ADD**: Além de copiar, também pode baixar arquivos de URLs.

```dockerfile
ADD https://example.com/app.zip /app/
```

##### WORKDIR (Define o diretório de trabalho)
Configura o diretório padrão para os comandos subsequentes.

```dockerfile
WORKDIR /app
```

##### CMD (Comando padrão do contêiner)
Define o comando executado quando o contêiner é iniciado.

```dockerfile
CMD ["python3", "app.py"]
```

- Apenas um CMD é permitido por Dockerfile; o último declarado será usado.

##### ENTRYPOINT (Comando principal do contêiner)
Semelhante ao CMD, mas permite que o contêiner seja configurado como executável.
Exemplo:

```dockerfile
ENTRYPOINT ["python3", "app.py"]
```

##### ENV (Variáveis de ambiente)
Define variáveis disponíveis para o contêiner.

```dockerfile
ENV PORT=8080
```

##### EXPOSE (Exposição de portas)
Indica que a aplicação no contêiner utiliza uma porta específica.

```dockerfile
EXPOSE 80
```

### Criando uma imagem com o `docker build`
Use o comando abaixo para criar uma imagem a partir do Dockerfile:

```bash
docker build -t nome-da-imagem .
```

- `-t nome-da-imagem`: Nomeia a imagem.
- `.`:Refere-se ao diretório onde o Dockerfile está localizado.

### Testando a imagem
Depois de criar a imagem, execute um contêiner com:

```bash
docker run -p 5000:5000 minha-aplicacao
```

- `-p 5000:5000`: Mapeia a porta 5000 do contêiner para a porta 5000 do host.

### Comandos úteis ao trabalhar com imagens

##### Lista imagens disponíveis
```bash
docker images
```

##### Removendo uma imagem
```bash
docker rmi nome-da-imagem
```

##### Inspecionar uma imagem
```bash
docker inspect nome-da-imagem
```



