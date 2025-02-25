# Урок 7: Използване на AWS Lambda за безсървърни функции

## Цели на урока
- Да разберем какво е AWS Lambda и концепцията за безсървърно изчисление
- Да се научим да създаваме и конфигурираме Lambda функции
- Да се запознаем с различните тригери за Lambda функции
- Да разберем как да наблюдаваме и дебъгваме Lambda функции
- Да създадем прост проект, използвайки Lambda и други AWS услуги

## Какво е AWS Lambda и безсървърно изчисление?

### Дефиниция на AWS Lambda
AWS Lambda е изчислителна услуга, която ви позволява да изпълнявате код без да осигурявате или управлявате сървъри. Lambda изпълнява вашия код само когато е необходимо и мащабира автоматично, от няколко заявки на ден до хиляди в секунда. Плащате само за изчислителното време, което консумирате - няма такса, когато кодът ви не се изпълнява.

### Концепция за безсървърно изчисление
Безсървърното изчисление е модел на облачно изпълнение, при който доставчикът на облачни услуги управлява динамично разпределението на машинни ресурси. Цената се базира на действителното количество ресурси, консумирани от приложението, а не на предварително закупен капацитет.

Ключови характеристики на безсървърното изчисление:
- **Без управление на сървъри** - разработчиците не се занимават с инфраструктура
- **Автоматично мащабиране** - приложенията се мащабират автоматично според натоварването
- **Плащане според използването** - таксуване само за реално използваните ресурси
- **Висока наличност** - вградена в платформата
- **Събитийно задвижвано** - функциите се изпълняват в отговор на събития

### Предимства на AWS Lambda
1. **Без управление на сървъри** - не се налага да осигурявате или поддържате сървъри
2. **Непрекъснато мащабиране** - автоматично мащабиране според нуждите
3. **Икономическа ефективност** - плащате само за изчислителното време, което използвате
4. **Бързина на изпълнение** - кодът може да започне да се изпълнява в рамките на милисекунди
5. **Интеграция с други AWS услуги** - лесна интеграция с други услуги като S3, DynamoDB, API Gateway и др.
6. **Поддръжка на множество езици** - поддържа различни програмни езици и рънтайми

### Ограничения на AWS Lambda
1. **Временно съхранение** - ограничено до 512 MB в `/tmp`
2. **Време за изпълнение** - максимум 15 минути
3. **Размер на пакета** - до 50 MB компресиран и 250 MB некомпресиран
4. **Памет** - от 128 MB до 10 GB
5. **Конкурентни изпълнения** - по подразбиране 1000 (може да се увеличи при поискване)
6. **Студен старт** - забавяне при първоначално изпълнение или след дълъг период на неактивност

## Поддържани езици и рънтайми в AWS Lambda

AWS Lambda поддържа множество програмни езици чрез използване на рънтайми. Рънтаймът предоставя специфична за езика среда, която изпълнява вашия код в Lambda.

### Основни поддържани езици:
1. **Node.js** (JavaScript)
2. **Python**
3. **Java**
4. **Go**
5. **.NET Core** (C#)
6. **Ruby**

### Избор на подходящ език
При избора на език за Lambda функция, обмислете:
- **Опит на екипа** - използвайте език, с който екипът ви е запознат
- **Време за студен старт** - езици като Python и Node.js имат по-бързо време за студен старт от Java или .NET
- **Екосистема** - наличие на библиотеки и инструменти
- **Производителност** - някои езици могат да бъдат по-ефективни за определени задачи
- **Интеграция** - съвместимост с други компоненти на вашето приложение

## Създаване и конфигуриране на Lambda функция

### Стъпки за създаване на Lambda функция чрез AWS Management Console

#### 1. Отворете Lambda конзолата
1. Влезте в AWS Management Console
2. Отидете на услугата "Lambda"
3. Кликнете "Create function"

#### 2. Изберете опция за създаване
1. Изберете "Author from scratch" за създаване на нова функция
2. Или изберете "Use a blueprint" за използване на предварително конфигуриран шаблон
3. Или изберете "Container image" за използване на контейнер
4. Или изберете "Browse serverless app repository" за използване на готово приложение

#### 3. Конфигурирайте основни настройки
1. Въведете име на функцията
2. Изберете рънтайм (например Node.js, Python, Java и т.н.)
3. Изберете архитектура (x86_64 или arm64)
4. Изберете или създайте роля за изпълнение с необходимите разрешения
5. Кликнете "Create function"

#### 4. Напишете код за функцията
След създаване на функцията, ще бъдете пренасочени към редактора на код, където можете да напишете или качите вашия код.

##### Пример за Node.js Lambda функция:
```javascript
exports.handler = async (event) => {
    console.log('Event: ', JSON.stringify(event, null, 2));
    
    const response = {
        statusCode: 200,
        body: JSON.stringify('Hello from Lambda!'),
    };
    
    return response;
};
```

##### Пример за Python Lambda функция:
```python
import json

def lambda_handler(event, context):
    print('Event: ', json.dumps(event))
    
    return {
        'statusCode': 200,
        'body': json.dumps('Hello from Lambda!')
    }
```

#### 5. Конфигурирайте настройки на функцията
1. **General configuration**:
   - Описание
   - Памет (от 128 MB до 10 GB)
   - Timeout (до 15 минути)
   - Ephemeral storage (до 10 GB)

2. **Permissions**:
   - Execution role - IAM роля, която определя какви AWS ресурси може да достъпва функцията

3. **Environment variables**:
   - Ключ-стойност двойки, достъпни за кода по време на изпълнение

4. **Tags**:
   - Метаданни за организиране и категоризиране на функцията

### Създаване на Lambda функция чрез AWS CLI

```bash
# Създаване на базова Lambda функция
aws lambda create-function \
  --function-name MyFunction \
  --runtime nodejs14.x \
  --role arn:aws:iam::123456789012:role/lambda-ex \
  --handler index.handler \
  --zip-file fileb://function.zip

# Актуализиране на код на функция
aws lambda update-function-code \
  --function-name MyFunction \
  --zip-file fileb://function.zip

# Актуализиране на конфигурация на функция
aws lambda update-function-configuration \
  --function-name MyFunction \
  --timeout 30 \
  --memory-size 256
```

### Създаване на Lambda функция чрез AWS SAM (Serverless Application Model)

AWS SAM е фреймуърк за изграждане на безсървърни приложения. Той опростява процеса на дефиниране на ресурси, необходими за безсървърни приложения.

#### 1. Инсталирайте AWS SAM CLI
```bash
# За macOS
brew install aws-sam-cli

# За Windows (с Chocolatey)
choco install aws-sam-cli

# За Linux
pip install aws-sam-cli
```

#### 2. Създайте нов SAM проект
```bash
sam init
```

#### 3. Изберете шаблон и конфигурирайте проекта
Следвайте интерактивните подкани, за да изберете рънтайм, име на проект и т.н.

#### 4. Структура на проекта
```
my-sam-app/
├── README.md
├── events/
│   └── event.json
├── hello-world/
│   ├── app.js
│   └── package.json
├── samconfig.toml
└── template.yaml
```

#### 5. Дефинирайте ресурси в template.yaml
```yaml
AWSTemplateFormatVersion: '2010-09-09'
Transform: AWS::Serverless-2016-10-31
Resources:
  HelloWorldFunction:
    Type: AWS::Serverless::Function
    Properties:
      CodeUri: hello-world/
      Handler: app.lambdaHandler
      Runtime: nodejs14.x
      Events:
        HelloWorld:
          Type: Api
          Properties:
            Path: /hello
            Method: get
```

#### 6. Изградете и разгърнете приложението
```bash
# Изграждане
sam build

# Разгръщане
sam deploy --guided
```

## Тригери за Lambda функции

Тригерите са услуги или ресурси, които извикват вашата Lambda функция. Lambda поддържа множество тригери, което позволява интеграция с различни AWS услуги.

### Основни типове тригери:

#### 1. API Gateway
- Създава REST или WebSocket API, която извиква Lambda функция
- Позволява създаване на HTTP endpoints за вашите функции
- Поддържа автентикация, авторизация, throttling и други функции

#### 2. S3
- Извиква Lambda функция при събития в S3 bucket (създаване, изтриване на обекти и т.н.)
- Полезно за обработка на файлове, генериране на миниатюри, извличане на метаданни и т.н.

#### 3. DynamoDB
- Извиква Lambda функция при промени в DynamoDB таблица
- Използва DynamoDB Streams за проследяване на промените
- Полезно за обработка на данни, агрегация, репликация и т.н.

#### 4. CloudWatch Events / EventBridge
- Извиква Lambda функция по график или при определени събития в AWS
- Позволява създаване на cron jobs или реакция на промени в състоянието на ресурси

#### 5. SNS (Simple Notification Service)
- Извиква Lambda функция при публикуване на съобщение в SNS тема
- Полезно за обработка на асинхронни съобщения и нотификации

#### 6. SQS (Simple Queue Service)
- Извиква Lambda функция при наличие на съобщения в опашка
- Полезно за обработка на задачи и разделяне на работни натоварвания

#### 7. Cognito
- Извиква Lambda функция при събития, свързани с потребителски акаунти
- Полезно за персонализирана автентикация и авторизация

### Добавяне на тригер към Lambda функция

#### Чрез AWS Management Console
1. Отворете Lambda конзолата и изберете вашата функция
2. Отидете на раздела "Configuration" и изберете "Triggers"
3. Кликнете "Add trigger"
4. Изберете тип на тригера от падащото меню
5. Конфигурирайте специфичните настройки за избрания тригер
6. Кликнете "Add"

#### Чрез AWS CLI
```bash
# Добавяне на S3 тригер
aws lambda create-event-source-mapping \
  --function-name MyFunction \
  --event-source-arn arn:aws:s3:::my-bucket \
  --batch-size 10

# Добавяне на DynamoDB тригер
aws lambda create-event-source-mapping \
  --function-name MyFunction \
  --event-source-arn arn:aws:dynamodb:us-east-1:123456789012:table/my-table/stream/2019-01-01T00:00:00.000 \
  --batch-size 100 \
  --starting-position LATEST
```

## Наблюдение и дебъгване на Lambda функции

### Наблюдение с CloudWatch Logs
Всяка Lambda функция автоматично интегрира с CloudWatch Logs, което позволява наблюдение на изпълнението.

#### Преглед на логове в AWS Management Console
1. Отворете Lambda конзолата и изберете вашата функция
2. Отидете на раздела "Monitor"
3. Кликнете "View logs in CloudWatch"
4. Прегледайте логовете, групирани по Log Streams

#### Добавяне на логове в кода
##### Node.js:
```javascript
exports.handler = async (event) => {
    console.log('Event received:', JSON.stringify(event));
    
    try {
        // Вашата логика тук
        console.log('Operation successful');
    } catch (error) {
        console.error('Error occurred:', error);
        throw error;
    }
    
    return { statusCode: 200, body: 'Success' };
};
```

##### Python:
```python
import json
import logging

logger = logging.getLogger()
logger.setLevel(logging.INFO)

def lambda_handler(event, context):
    logger.info(f'Event received: {json.dumps(event)}')
    
    try:
        # Вашата логика тук
        logger.info('Operation successful')
    except Exception as e:
        logger.error(f'Error occurred: {str(e)}')
        raise
    
    return {
        'statusCode': 200,
        'body': 'Success'
    }
```

### Наблюдение с CloudWatch Metrics
CloudWatch автоматично събира метрики за вашите Lambda функции.

#### Основни метрики:
- **Invocations** - брой пъти, когато функцията е била извикана
- **Duration** - време за изпълнение на функцията
- **Errors** - брой изпълнения, завършили с грешка
- **Throttles** - брой заявки, които са били ограничени поради достигане на лимит
- **ConcurrentExecutions** - брой едновременни изпълнения
- **IteratorAge** - възраст на последния запис, обработен от функцията (за stream-базирани тригери)

#### Създаване на аларми
1. Отворете CloudWatch конзолата
2. Отидете на "Alarms" > "Create alarm"
3. Кликнете "Select metric"
4. Изберете "Lambda" > "By Function Name"
5. Изберете метрика (например Errors)
6. Конфигурирайте условието за алармата
7. Конфигурирайте действия при аларма (например SNS нотификация)
8. Задайте име и описание
9. Кликнете "Create alarm"

### Дебъгване на Lambda функции

#### Локално тестване с AWS SAM
AWS SAM CLI позволява локално тестване на Lambda функции преди разгръщане.

```bash
# Локално извикване на функция с тестово събитие
sam local invoke -e events/event.json

# Стартиране на локален API Gateway за тестване на HTTP endpoints
sam local start-api
```

#### Използване на X-Ray за трасиране
AWS X-Ray помага за анализ и дебъгване на разпределени приложения.

1. Активирайте X-Ray в настройките на функцията
2. Добавете AWS X-Ray SDK към вашия код

##### Node.js:
```javascript
const AWSXRay = require('aws-xray-sdk-core');
const AWS = AWSXRay.captureAWS(require('aws-sdk'));

exports.handler = async (event) => {
    // X-Ray ще проследи всички AWS SDK извиквания
    const s3 = new AWS.S3();
    const result = await s3.listBuckets().promise();
    
    return { statusCode: 200, body: JSON.stringify(result) };
};
```

##### Python:
```python
import boto3
from aws_xray_sdk.core import xray_recorder
from aws_xray_sdk.core import patch_all

patch_all()  # Patch all supported libraries

def lambda_handler(event, context):
    # X-Ray ще проследи всички boto3 извиквания
    s3 = boto3.client('s3')
    result = s3.list_buckets()
    
    return {
        'statusCode': 200,
        'body': str(result)
    }
```

#### Използване на AWS Lambda Power Tuning
AWS Lambda Power Tuning е инструмент с отворен код, който помага за оптимизиране на настройките на Lambda функции (памет, CPU) за най-добро съотношение цена/производителност.

1. Разгърнете AWS Lambda Power Tuning в акаунта си
2. Изпълнете инструмента срещу вашата функция
3. Анализирайте резултатите и изберете оптималната конфигурация

## Практически проект: Създаване на система за обработка на изображения

В този проект ще създадем система за обработка на изображения, използвайки AWS Lambda, S3 и DynamoDB.

### Архитектура на проекта
1. Потребителят качва изображение в S3 bucket
2. S3 събитието задейства Lambda функция
3. Lambda функцията обработва изображението (преоразмеряване, добавяне на воден знак и т.н.)
4. Lambda функцията запазва обработеното изображение в друг S3 bucket
5. Lambda функцията записва метаданни за изображението в DynamoDB

### Стъпка 1: Създаване на S3 buckets
1. Създайте два S3 bucket:
   - `image-upload-bucket` - за оригинални изображения
   - `image-processed-bucket` - за обработени изображения

### Стъпка 2: Създаване на DynamoDB таблица
1. Създайте DynamoDB таблица с име `ImageMetadata`
2. Задайте `imageId` като partition key

### Стъпка 3: Създаване на IAM роля за Lambda
1. Създайте IAM роля с следните разрешения:
   - `AWSLambdaBasicExecutionRole` - за CloudWatch Logs
   - `AmazonS3ReadOnlyAccess` - за четене от S3
   - `AmazonS3FullAccess` - за запис в S3
   - `AmazonDynamoDBFullAccess` - за запис в DynamoDB

### Стъпка 4: Създаване на Lambda функция (Node.js)

```javascript
const AWS = require('aws-sdk');
const sharp = require('sharp');
const s3 = new AWS.S3();
const dynamodb = new AWS.DynamoDB.DocumentClient();
const { v4: uuidv4 } = require('uuid');

exports.handler = async (event) => {
    try {
        // Извличане на информация за S3 събитието
        const bucket = event.Records[0].s3.bucket.name;
        const key = decodeURIComponent(event.Records[0].s3.object.key.replace(/\+/g, ' '));
        
        console.log(`Processing image from bucket: ${bucket}, key: ${key}`);
        
        // Извличане на изображението от S3
        const s3Object = await s3.getObject({
            Bucket: bucket,
            Key: key
        }).promise();
        
        // Обработка на изображението с Sharp
        const originalImage = s3Object.Body;
        const resizedImage = await sharp(originalImage)
            .resize(800, 600) // Преоразмеряване до 800x600
            .toBuffer();
        
        // Генериране на уникален ID за изображението
        const imageId = uuidv4();
        const processedKey = `processed-${imageId}-${key}`;
        
        // Качване на обработеното изображение в целевия bucket
        await s3.putObject({
            Bucket: 'image-processed-bucket',
            Key: processedKey,
            Body: resizedImage,
            ContentType: 'image/jpeg'
        }).promise();
        
        console.log(`Processed image saved to: image-processed-bucket/${processedKey}`);
        
        // Записване на метаданни в DynamoDB
        await dynamodb.put({
            TableName: 'ImageMetadata',
            Item: {
                imageId: imageId,
                originalBucket: bucket,
                originalKey: key,
                processedBucket: 'image-processed-bucket',
                processedKey: processedKey,
                processedAt: new Date().toISOString(),
                size: resizedImage.length
            }
        }).promise();
        
        console.log('Metadata saved to DynamoDB');
        
        return {
            statusCode: 200,
            body: JSON.stringify({
                message: 'Image processed successfully',
                imageId: imageId
            })
        };
    } catch (error) {
        console.error('Error processing image:', error);
        throw error;
    }
};
```

### Стъпка 5: Пакетиране на Lambda функцията
1. Създайте нова директория за проекта
2. Инициализирайте npm проект и инсталирайте зависимостите:
   ```bash
   mkdir image-processor && cd image-processor
   npm init -y
   npm install sharp uuid aws-sdk
   ```
3. Създайте файл `index.js` с кода на функцията
4. Пакетирайте функцията:
   ```bash
   zip -r function.zip index.js node_modules
   ```

### Стъпка 6: Създаване на Lambda функция
1. Създайте Lambda функция с име `ImageProcessor`
2. Качете ZIP файла като код на функцията
3. Задайте `index.handler` като handler
4. Изберете създадената IAM роля
5. Увеличете timeout до 30 секунди и памет до 512 MB

### Стъпка 7: Добавяне на S3 тригер
1. Добавете тригер към Lambda функцията
2. Изберете `image-upload-bucket` като източник
3. Задайте събитие тип `All object create events`
4. Запазете тригера

### Стъпка 8: Тестване на системата
1. Качете изображение в `image-upload-bucket`
2. Проверете логовете на Lambda функцията в CloudWatch
3. Проверете дали обработеното изображение е запазено в `image-processed-bucket`
4. Проверете дали метаданните са записани в DynamoDB таблицата

## Допълнителни ресурси
- [AWS Lambda Documentation](https://docs.aws.amazon.com/lambda/)
- [AWS Serverless Application Model (SAM)](https://docs.aws.amazon.com/serverless-application-model/)
- [AWS Lambda Best Practices](https://docs.aws.amazon.com/lambda/latest/dg/best-practices.html)
- [AWS Lambda Power Tuning](https://github.com/alexcasalboni/aws-lambda-power-tuning)
- [Serverless Framework](https://www.serverless.com/)

## Въпроси за дискусия
1. Какви са предимствата и недостатъците на безсървърната архитектура спрямо традиционната сървърна архитектура?
2. Как бихте решили проблема със "студения старт" при Lambda функции?
3. Какви типове приложения са най-подходящи за безсървърна архитектура и кои не са?
