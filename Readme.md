# Projeto de Demonstração da Pilha ELK com Spring Boot

<p align="center"><h3>Apoie o projeto</h3></p>

<p align="center">
  <a href="https://www.paypal.com/donate/?business=3YHDFH2J8SHEG&no_recurring=0&currency_code=USD">
    <img src="https://img.shields.io/badge/paypal-support-blue.svg"/>
  </a>
</p>

Este projeto demonstra o uso prático da pilha ELK (Elasticsearch, Logstash e Kibana) em conjunto com uma aplicação Spring Boot 3.

> **Atenção:** Este projeto está configurado sem as boas práticas de segurança, sendo recomendado exclusivamente para fins didáticos. Para uso em produção, é essencial habilitar e configurar adequadamente a segurança em todos os componentes envolvidos.

---

## 🚀 Tecnologias utilizadas

- Docker (versão 20 ou superior)
- Spring Boot 3
- Elasticsearch 7.17
- Logstash 7.17
- Kibana 7.17

---

## 📂 Estrutura do Projeto

O projeto inclui os seguintes componentes:

- **Aplicação Spring Boot**: gera logs e os envia ao Logstash.
- **Logstash**: recebe logs via TCP, realiza processamento e encaminha ao Elasticsearch.
- **Elasticsearch**: armazena os logs recebidos do Logstash.
- **Kibana**: fornece interface gráfica para visualização e análise dos logs armazenados no Elasticsearch.

---

### 📌 Nome do índice utilizado:

```
otel.mpa-%{+YYYY.MM.dd}
```

![logstash.png](asset/logstash.png)

---

## ✅ Executando o projeto

### 1. Inicie os containers com Docker Compose

```bash
docker-compose up --build
```

### 2. Teste o endpoint da aplicação Spring Boot

```bash
curl http://localhost:8080/hello
```

Este comando gera logs automaticamente enviados ao Logstash.

---

## 📊 Visualizando os logs no Kibana

Abra o Kibana no navegador acessando:

```
http://localhost:5601
```

No primeiro acesso, é necessário criar um índice no Kibana para visualizar os logs.

### Passos para criar o índice:

![create-index-kibana-1.png](asset/create-index-kibana-1.png)
![create-index-kibana-2.png](asset/create-index-kibana-2.png)

Após criado, você poderá consultar os logs em:

```
http://localhost:5601/app/discover
```

![kibana_iu.png](asset/kibana_iu.png)

---