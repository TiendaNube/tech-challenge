# PT-BR 🇧🇷
# Tech Challenge
O desafio consiste em implementar novas **API's** para trabalhar com as transações de nossos merchants (vendedores),
para isso vamos utilizar algumas API's disponíveis nesse repositório.

## Nós precisamos que você implemente:

1. Um endpoint para processar transações e pagamentos de um determinado merchant (vendedor)
  * Uma transação deve conter pelo menos:
  	* O valor total da transação, formatado em string decimal
  	* Descrição da transação, por exemplo "T-Shirt Black M"
  	* Método de pagamento: **debit_card** ou **credit_card**
  	* O número do cartão (devemos armazenar e retornar somente os últimos 4 dígitos do cartão, por ser uma informação sensível)
  	* O nome do dono do cartão
  	* Data de Expiração
  	* CVV do cartão

* Ao criar uma transação, também deve ser criado um **recebível** do merchant (**payables**), com as seguintes regras de negócio:
  * **Debit card**:
      * O payable deve ser criado com **status = paid**, indicando que o merchant irá receber o valor
      * O payable deve ser criado com a data igual a data de criação (D + 0).

  * **Credit card**:
      * O payable deve ser criado com **status = waiting_funds**, indicando que o merchant irá receber esse valor no futuro
      * O Payable deve ser criado com a data igual a data de criação da transação  + 30 dias (D + 30)

  * Ao criar payables, devemos descontar uma taxa de processamento (chamada de `fee`). Considere **2%** para transações **debit_card**
e **4%** para transações **credit_card**. Exemplo: Quando um payable é criado no valor de R$ 100,00 a partir de uma transação **credit_card**  ele receberá R$ 96,00.

2. Um endpoint que calcule o total de Recebíveis (payables) do merchant por período, a resposta deve conter:
  * Valor total de recebíveis pagos
  * Total cobrado de taxa nos recebíveis pagos
  * Valor a receber para o futuro

## Importante
Não utilizaremos banco de dados nesta aplicação. Todas as informações deverão ser armazenadas na **Mock API** que está no docker deste projeto. Você consumirá os endpoints do container como microsserviços

## Extra
- Você pode utilizar qualquer linguagem de programação (recomendamos que utilize a que você possui maior familiaridade), frameworks e biblioteca
- É um diferencial que pelo menos a lógica principal seja testada

# Instalação
Requisito é ter docker em sua máquina para rodar nossa API de mock:

```
docker-compose up
```

## Mock API
Com o serviço executando você poderá utilizar as seguintes API's:

---

## Transactions
Listagem de `transactions` registradas
`GET http://0.0.0.0:8080/transactions`

Carregamento de uma `transaction` específica
`GET http://0.0.0.0:8080/transactions/:id`

Criação de `transactions`
`POST http://0.0.0.0:8080/transactions`

Remoção de `transaction` por ID
`DELETE http://0.0.0.0:8080/transactions/:id`

---

## Payables
Listagem de `payables` registradas
`GET http://0.0.0.0:8080/payables`

Carregamento de um `payable` específica
`GET http://0.0.0.0:8080/payables/:id`

Criação de `payables`
`POST http://0.0.0.0:8080/payables`

Remoção de `payable` por ID
`DELETE http://0.0.0.0:8080/payables/:id`

# ES-AR 🇦🇷
# Tech Challenge
El desafío consiste en implementar nuevas **API's** para manejar las transacciones de nuestros merchants,
para eso vamos a usar algunas API's que están disponibles en ese repositorio.

## Necesitamos que implementes:

1. Un endpoint para procesar transacciones y pagos de un merchant (vendedor)
  * Una transacción debe tener:
  	* El valor total de la transacción, formateado en string decimal
  	* Descripción de la transacción, por ejemplo "T-Shirt Black M"
  	* Método de pago: **debit_card** o **credit_card**
  	* El número de la tarjeta (debemos guardar y devolver solamente los últimos 4 dígitos de la tarjeta, por ser información delicada)
  	* El nombre del dueño de la tarjeta
  	* Fecha de expiración
  	* CVV de la tarjeta

* Al crear una transacción, también debe ser creada una cuenta por cobrar del merchant (payables), con las siguientes reglas de negocio:
  * Transacción **Debit card**:
      * El payable debe ser creado con **status = paid**, indicando que el merchant recebirá el valor
      * El payable debe ser creado con la fecha igual a la fecha de creación (D + 0).

  * Transacción **Credit card**:
      * El payable debe ser creado con  **status = waiting_funds**, indicando que el merchant irá recibir ese valor en el futuro
      * El payable debe ser creado con la fecha igual a la fecha de creación + 30 días (D + 30)

  * Al crear payables, debemos descontar la tasa de procesamiento (llamada de `fee`). Se debe considerar **2%** para transacciones **debit_card**
y **4%** para transacciones **credit_card**. Ejemplo: Cuando un payable es creado con un valor de ARS 100,00 a partir de una transacción **credit_card**  él recibirá ARS 96,00.

2. Un endpoint que calcule el total de cuentas por cobrar (payables) del merchant por período, la respuesta debe contener:
  * Valor total pago de cuentas por cobrar
  * Total cobrado de tasas en los pagos
  * Valor de futuros ingresos
  

## Importante
No utilizaremos base de datos en esa aplicación. Toda la información deberán ser grabadas en la **Mock API** que está en el docker de este proyecto. Vas a consumir los endpoints del container como microservicios.

## Extra
- Podrás usar cualquier lenguage de programación (te recomendamos que utilizes el que mejor manejás), frameworks e librerías.
- Es un diferencial que por lo menos la lógica principal sea testeada.

# Instalación
Es un requisito tener docker en tu computadora para correr nuestra API de mock:

```
docker-compose up
```

## Mock API
Con el servicio corriendo podrás usar las seguientes API's:

---

## Transactions
Listado de `transactions` registradas
`GET http://0.0.0.0:8080/transactions`

Detalle de una `transaction` específica
`GET http://0.0.0.0:8080/transactions/:id`

Creación de `transactions`
`POST http://0.0.0.0:8080/transactions`

Borrado de `transaction` por ID
`DELETE http://0.0.0.0:8080/transactions/:id`

---

## Payables
Listado de `payables` registrados
`GET http://0.0.0.0:8080/payables`

Detalle de un `payable` específico
`GET http://0.0.0.0:8080/payables/:id`

Creación de `payables`
`POST http://0.0.0.0:8080/payables`

Borrado de `payable` por ID
`DELETE http://0.0.0.0:8080/payables/:id`

