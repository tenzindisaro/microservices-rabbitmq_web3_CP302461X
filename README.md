# 📦 Microservices com Spring Boot + RabbitMQ

Este projeto implementa uma arquitetura de **microsserviços** utilizando **Spring Boot** e comunicação assíncrona com **RabbitMQ (CloudAMQP)**.

---

## 🚀 Tecnologias utilizadas

* Java 17
* Spring Boot
* Spring Data JPA
* MySQL
* RabbitMQ (CloudAMQP)
* Spring AMQP
* Java Mail Sender

---

## 🏗️ Estrutura do projeto

O sistema é composto por dois microsserviços:

```
microservices-rabbitmq
 ├── user   → cadastro de usuários
 └── email  → envio de emails
```

---

## 🔄 Funcionamento

1. O cliente envia uma requisição para criar um usuário:

```
POST /users
```

2. O **user-service**:

* salva o usuário no banco
* envia uma mensagem para o RabbitMQ

3. O **email-service**:

* consome a mensagem da fila
* envia um email
* salva o status no banco

---

## 🐰 RabbitMQ

A comunicação entre os serviços é feita de forma **assíncrona** usando filas.

```
User Service → RabbitMQ → Email Service
```

---

## 📧 Envio de Email

O envio é realizado via **SMTP do Gmail**, utilizando senha de aplicativo.

---

## ▶️ Como executar

1. Inicie o banco MySQL
2. Configure os arquivos `application.properties`
3. Execute os serviços:

### User Service

```
porta: 8081
```

### Email Service

```
porta: 8082
```

4. Teste com:

```
POST http://localhost:8081/users
```

---

## ✅ Resultado esperado

* Usuário salvo no banco `ms_user`
* Mensagem enviada ao RabbitMQ
* Email enviado ao usuário
* Registro salvo no banco `ms_email`

---

## 📌 Autor

Projeto desenvolvido para fins acadêmicos.
