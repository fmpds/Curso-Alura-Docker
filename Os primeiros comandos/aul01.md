# Anotações do Curso

## O que é o Docker?

O Docker é uma plataforma de software que permite criar, gerenciar e executar contêineres.

- **Contêiner:** Uma unidade leve e portátil que inclui tudo o que um software precisa para rodar (código, bibliotecas, dependências, etc.).
- Ele isola a aplicação do sistema operacional subjacente, garantindo que ela funcione de forma consistente, independentemente do ambiente.

## Por que usar Docker?

1. **Portabilidade**: "Funciona no meu computador" se aplica a qualquer máquina com Docker.
2. **Isolamento**: Contêineres compartilham o mesmo kernel do sistema, mas não interferem uns nos outros.
3. **Eficiência**: Mais leve que máquinas virtuais porque não precisa de um sistema operacional completo para cada contêiner.
4. **Agilidade no desenvolvimento**: Fácil de montar ambientes de desenvolvimento e produção idênticos.

## Conceitos básicos do Docker

##### 1.Imagem (Image)

Uma imagem é como um "template" para criar contêineres.

- Contém o sistema de arquivos necessário e o código da aplicação.
- Exemplo: Uma imagem pode ter o Ubuntu e um servidor Nginx configurado.

##### 2.Contêiner (Container)

Um contêiner é uma instância em execução de uma imagem.

- Você pode criar vários contêineres da mesma imagem.
- São efêmeros (podem ser destruídos e recriados rapidamente).

##### 3. Dockerfile

Um arquivo de texto que contém instruções para criar uma imagem.
Exemplo de um Dockerfile para uma aplicação em Python:

```dockerfile
# Use uma imagem base
FROM python:3.9-slim

# Copie o código da aplicação
COPY app.py /app.py

# Instale dependências
RUN pip install flask

# Comando para rodar a aplicação
CMD ["python", "app.py"]
```

##### 4. Docker Hub

Um repositório online onde você pode buscar ou armazenar imagens Docker.

- Comando para buscar imagem:
 ```bash
 docker pull nginx
 ```

 ##### 5. Volume
 
 Permite armazenar dados fora do contêiner.

- Útil para persistir dados entre reinicializações do contêiner.