# Урок 8: Използване на DynamoDB за NoSQL бази данни

## Цели на урока
- Да разберем какво е Amazon DynamoDB и как работи
- Да се научим да създаваме и конфигурираме DynamoDB таблици
- Да се запознаем с основните операции в DynamoDB (CRUD)
- Да разберем как да използваме индекси за оптимизация на заявки
- Да създадем прост проект, използвайки DynamoDB и други AWS услуги

## Какво е Amazon DynamoDB и как работи?

### Дефиниция на Amazon DynamoDB
Amazon DynamoDB е напълно управлявана NoSQL база данни, която поддържа ключ-стойност и документи модели на данни. Тя е проектирана да осигурява бърза и предсказуема производителност с безкрайна мащабируемост. DynamoDB автоматично разпределя данните и трафика на таблицата върху достатъчен брой сървъри, за да се справи с всяко ниво на заявките.

### Основни концепции на DynamoDB
- **Таблици** - основните контейнери за данни в DynamoDB. Всяка таблица има уникално име.
- **Елементи** - записи в таблицата, аналогични на редове в релационна база данни.
- **Атрибути** - полета в елементите, аналогични на колони в релационна база данни.
- **Ключове** - уникални идентификатори за елементите в таблицата.
- **Първичен ключ** - уникален идентификатор за всеки елемент в таблицата. Може да бъде:
  - **Ключ на партиция** (Partition Key) - единствен атрибут, който определя уникалността на елемента.
  - **Съставен ключ** (Composite Key) - комбинация от ключ на партиция и ключ на сортиране (Sort Key).
- **Индекси** - структури, които подобряват производителността на заявките. Могат да бъдат:
  - **Глобални вторични индекси (GSI)** - индекси, които могат да бъдат създадени върху всякакви атрибути.
  - **Локални вторични индекси (LSI)** - индекси, които могат да бъдат създадени върху атрибути, различни от ключа на сортиране.

### Как работи DynamoDB?
1. **Създавате таблица** - дефинирате структурата на таблицата и първичния ключ.
2. **Добавяте елементи** - вмъквате записи в таблицата.
3. **Извършвате заявки** - четете данни от таблицата, използвайки ключове и индекси.
4. **Актуализирате елементи** - променяте съществуващи записи.
5. **Изтривате елементи** - премахвате записи от таблицата.
6. **Управлявате капацитет** - конфигурирате капацитета за четене и запис на таблицата.

## Създаване и конфигуриране на DynamoDB таблица

### Стъпки за създаване на DynamoDB таблица чрез AWS Management Console

#### 1. Отворете DynamoDB конзолата
1. Влезте в AWS Management Console
2. Отидете на услугата "DynamoDB"
3. Кликнете "Create table"

#### 2. Конфигурирайте основни настройки
1. Въведете име на таблицата
2. Изберете тип на първичния ключ:
   - **Partition key** - единствен атрибут (например `UserId`)
   - **Partition key and sort key** - комбинация от два атрибута (например `UserId` и `Timestamp`)
3. Кликнете "Next"

#### 3. Конфигурирайте капацитет и настройки
1. Изберете режим на капацитет:
   - **Provisioned** - задавате фиксиран капацитет за четене и запис
   - **On-demand** - автоматично мащабиране според натоварването
2. Конфигурирайте допълнителни настройки (опционално):
   - **Encryption** - криптиране на данните
   - **Point-in-time recovery** - възстановяване на данни до определен момент
   - **Time to live (TTL)** - автоматично изтриване на стари данни
   - **Tags** - добавяне на метаданни към таблицата
3. Кликнете "Create"

### Конфигуриране на индекси

#### Глобални вторични индекси (GSI)
GSI позволяват създаване на индекси върху атрибути, различни от първичния ключ. Те подобряват производителността на заявките.

1. В DynamoDB конзолата, изберете вашата таблица
2. Отидете на раздела "Indexes"
3. Кликнете "Create index"
4. Въведете име на индекса
5. Изберете атрибути за ключ на партиция и ключ на сортиране (опционално)
6. Конфигурирайте капацитет за индекса (ако използвате provisioned режим)
7. Кликнете "Create index"

#### Локални вторични индекси (LSI)
LSI позволяват създаване на индекси върху атрибути, различни от ключа на сортиране. Те подобряват производителността на заявките.

1. В DynamoDB конзолата, изберете вашата таблица
2. Отидете на раздела "Indexes"
3. Кликнете "Create index"
4. Въведете име на индекса
5. Изберете атрибут за ключ на сортиране
6. Конфигурирайте капацитет за индекса (ако използвате provisioned режим)
7. Кликнете "Create index"

## Основни операции в DynamoDB (CRUD)

### Създаване на елементи (Create)

#### Чрез AWS Management Console
1. В DynamoDB конзолата, изберете вашата таблица
2. Отидете на раздела "Items"
3. Кликнете "Create item"
4. Въведете стойности за атрибутите на елемента
5. Кликнете "Save"

#### Чрез AWS CLI
```bash
aws dynamodb put-item \
  --table-name YourTableName \
  --item '{
    "UserId": {"S": "user123"},
    "Name": {"S": "John Doe"},
    "Email": {"S": "john.doe@example.com"}
  }'
```

### Четене на елементи (Read)

#### Чрез AWS Management Console
1. В DynamoDB конзолата, изберете вашата таблица
2. Отидете на раздела "Items"
3. Използвайте филтри за търсене на елементи по атрибути

#### Чрез AWS CLI
```bash
# Получаване на елемент по ключ
aws dynamodb get-item \
  --table-name YourTableName \
  --key '{"UserId": {"S": "user123"}}'

# Сканиране на таблица
aws dynamodb scan \
  --table-name YourTableName

# Заявка по индекс
aws dynamodb query \
  --table-name YourTableName \
  --index-name YourIndexName \
  --key-condition-expression "Email = :email" \
  --expression-attribute-values '{":email": {"S": "john.doe@example.com"}}'
```

### Актуализиране на елементи (Update)

#### Чрез AWS Management Console
1. В DynamoDB конзолата, изберете вашата таблица
2. Отидете на раздела "Items"
3. Изберете елемента, който искате да актуализирате
4. Кликнете "Edit"
5. Променете стойностите на атрибутите
6. Кликнете "Save"

#### Чрез AWS CLI
```bash
aws dynamodb update-item \
  --table-name YourTableName \
  --key '{"UserId": {"S": "user123"}}' \
  --update-expression "SET Email = :email" \
  --expression-attribute-values '{":email": {"S": "new.email@example.com"}}'
```

### Изтриване на елементи (Delete)

#### Чрез AWS Management Console
1. В DynamoDB конзолата, изберете вашата таблица
2. Отидете на раздела "Items"
3. Изберете елемента, който искате да изтриете
4. Кликнете "Delete"
5. Потвърдете изтриването

#### Чрез AWS CLI
```bash
aws dynamodb delete-item \
  --table-name YourTableName \
  --key '{"UserId": {"S": "user123"}}'
```

## Използване на индекси за оптимизация на заявки

### Глобални вторични индекси (GSI)
GSI позволяват създаване на индекси върху атрибути, различни от първичния ключ. Те подобряват производителността на заявките.

#### Пример за създаване на GSI
```bash
aws dynamodb update-table \
  --table-name YourTableName \
  --attribute-definitions AttributeName=Email,AttributeType=S \
  --global-secondary-index-updates \
    '[{"Create":{"IndexName":"EmailIndex","KeySchema":[{"AttributeName":"Email","KeyType":"HASH"}],"Projection":{"ProjectionType":"ALL"},"ProvisionedThroughput":{"ReadCapacityUnits":5,"WriteCapacityUnits":5}}}]'
```

### Локални вторични индекси (LSI)
LSI позволяват създаване на индекси върху атрибути, различни от ключа на сортиране. Те подобряват производителността на заявките.

#### Пример за създаване на LSI
```bash
aws dynamodb update-table \
  --table-name YourTableName \
  --attribute-definitions AttributeName=Timestamp,AttributeType=N \
  --local-secondary-index-updates \
    '[{"Create":{"IndexName":"TimestampIndex","KeySchema":[{"AttributeName":"UserId","KeyType":"HASH"},{"AttributeName":"Timestamp","KeyType":"RANGE"}],"Projection":{"ProjectionType":"ALL"}}}]'
```

## Практически проект: Създаване на система за управление на задачи

В този проект ще създадем система за управление на задачи, използвайки DynamoDB и други AWS услуги.

### Архитектура на проекта
1. Потребителят създава задача чрез уеб интерфейс
2. Данните за задачата се записват в DynamoDB таблица
3. Потребителят може да преглежда, актуализира и изтрива задачи

### Стъпка 1: Създаване на DynamoDB таблица
1. Създайте таблица с име `Tasks`
2. Задайте `TaskId` като partition key
3. Задайте `UserId` като sort key

### Стъпка 2: Създаване на IAM роля за Lambda
1. Създайте IAM роля с следните разрешения:
   - `AWSLambdaBasicExecutionRole` - за CloudWatch Logs
   - `AmazonDynamoDBFullAccess` - за достъп до DynamoDB

### Стъпка 3: Създаване на Lambda функции

#### Функция за създаване на задача (Node.js)
```javascript
const AWS = require('aws-sdk');
const dynamodb = new AWS.DynamoDB.DocumentClient();
const { v4: uuidv4 } = require('uuid');

exports.handler = async (event) => {
    const { userId, title, description } = JSON.parse(event.body);
    const taskId = uuidv4();
    
    const params = {
        TableName: 'Tasks',
        Item: {
            TaskId: taskId,
            UserId: userId,
            Title: title,
            Description: description,
            CreatedAt: new Date().toISOString()
        }
    };
    
    await dynamodb.put(params).promise();
    
    return {
        statusCode: 201,
        body: JSON.stringify({ message: 'Task created', taskId })
    };
};
```

#### Функция за четене на задачи (Node.js)
```javascript
const AWS = require('aws-sdk');
const dynamodb = new AWS.DynamoDB.DocumentClient();

exports.handler = async (event) => {
    const { userId } = event.queryStringParameters;
    
    const params = {
        TableName: 'Tasks',
        KeyConditionExpression: 'UserId = :userId',
        ExpressionAttributeValues: {
            ':userId': userId
        }
    };
    
    const result = await dynamodb.query(params).promise();
    
    return {
        statusCode: 200,
        body: JSON.stringify(result.Items)
    };
};
```

#### Функция за актуализиране на задача (Node.js)
```javascript
const AWS = require('aws-sdk');
const dynamodb = new AWS.DynamoDB.DocumentClient();

exports.handler = async (event) => {
    const { taskId, userId, title, description } = JSON.parse(event.body);
    
    const params = {
        TableName: 'Tasks',
        Key: {
            TaskId: taskId,
            UserId: userId
        },
        UpdateExpression: 'SET Title = :title, Description = :description',
        ExpressionAttributeValues: {
            ':title': title,
            ':description': description
        }
    };
    
    await dynamodb.update(params).promise();
    
    return {
        statusCode: 200,
        body: JSON.stringify({ message: 'Task updated' })
    };
};
```

#### Функция за изтриване на задача (Node.js)
```javascript
const AWS = require('aws-sdk');
const dynamodb = new AWS.DynamoDB.DocumentClient();

exports.handler = async (event) => {
    const { taskId, userId } = JSON.parse(event.body);
    
    const params = {
        TableName: 'Tasks',
        Key: {
            TaskId: taskId,
            UserId: userId
        }
    };
    
    await dynamodb.delete(params).promise();
    
    return {
        statusCode: 200,
        body: JSON.stringify({ message: 'Task deleted' })
    };
};
```

### Стъпка 4: Пакетиране на Lambda функции
1. Създайте нова директория за всяка функция
2. Инициализирайте npm проект и инсталирайте зависимостите:
   ```bash
   mkdir create-task && cd create-task
   npm init -y
   npm install aws-sdk uuid
   # Създайте index.js с кода на функцията
   zip -r function.zip index.js node_modules
   ```

### Стъпка 5: Създаване на Lambda функции
1. Създайте Lambda функции за създаване, четене, актуализиране и изтриване на задачи
2. Качете ZIP файловете като код на функциите
3. Задайте `index.handler` като handler
4. Изберете създадената IAM роля
5. Увеличете timeout до 30 секунди и памет до 512 MB

### Стъпка 6: Създаване на API Gateway
1. Създайте нов REST API в API Gateway
2. Създайте ресурси и методи за създаване, четене, актуализиране и изтриване на задачи
3. Интегрирайте методите с Lambda функциите

### Стъпка 7: Тестване на системата
1. Използвайте Postman или друг инструмент за тестване на API
2. Създайте, прочетете, актуализирайте и изтрийте задачи чрез API
3. Проверете данните в DynamoDB таблицата

## Допълнителни ресурси
- [Amazon DynamoDB Documentation](https://docs.aws.amazon.com/dynamodb/)
- [Amazon DynamoDB Best Practices](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html)
- [AWS Lambda Documentation](https://docs.aws.amazon.com/lambda/)
- [AWS API Gateway Documentation](https://docs.aws.amazon.com/apigateway/)
- [AWS SDK for JavaScript](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/)

## Въпроси за дискусия
1. Какви са предимствата и недостатъците на NoSQL базите данни спрямо релационните бази данни?
2. Как бихте избрали подходящ тип база данни за вашето приложение?
3. Какви мерки за сигурност бихте предприели за защита на данните в DynamoDB?
