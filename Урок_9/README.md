# Урок 9: Използване на Amazon RDS за релационни бази данни

## Цели на урока
- Да разберем какво е Amazon RDS и как работи
- Да се научим да създаваме и конфигурираме RDS инстанции
- Да се запознаем с различните типове бази данни, поддържани от RDS
- Да разберем как да управляваме сигурността и резервните копия на RDS
- Да създадем прост проект, използвайки RDS и други AWS услуги

## Какво е Amazon RDS и как работи?

### Дефиниция на Amazon RDS
Amazon Relational Database Service (RDS) е управлявана услуга за релационни бази данни, която улеснява настройката, работата и мащабирането на релационни бази данни в облака. Тя автоматизира задачи като хардуерно осигуряване, настройка на базата данни, пачване и архивиране, което ви позволява да се фокусирате върху вашите приложения.

### Основни концепции на RDS
- **Инстанции** - виртуални сървъри, на които се изпълняват базите данни.
- **Бази данни** - колекции от данни, организирани в таблици.
- **Типове бази данни** - различни релационни бази данни, поддържани от RDS (например MySQL, PostgreSQL, MariaDB, Oracle, SQL Server).
- **Сигурност** - механизми за защита на данните, включително мрежова сигурност и криптиране.
- **Резервни копия** - автоматични и ръчни резервни копия на базите данни.
- **Мащабиране** - възможност за увеличаване или намаляване на ресурсите според нуждите.

### Как работи RDS?
1. **Създавате RDS инстанция** - избирате тип база данни, конфигурирате настройки и стартирате инстанцията.
2. **Свързвате се с базата данни** - използвате стандартни инструменти и библиотеки за връзка с базата данни.
3. **Управлявате базата данни** - изпълнявате SQL заявки, създавате таблици, вмъквате данни и т.н.
4. **Осигурявате сигурност** - конфигурирате мрежова сигурност, потребители и роли.
5. **Архивирате данни** - създавате автоматични и ръчни резервни копия.
6. **Мащабирате ресурси** - увеличавате или намалявате капацитета на инстанцията според нуждите.

## Създаване и конфигуриране на RDS инстанция

### Стъпки за създаване на RDS инстанция чрез AWS Management Console

#### 1. Отворете RDS конзолата
1. Влезте в AWS Management Console
2. Отидете на услугата "RDS"
3. Кликнете "Create database"

#### 2. Изберете тип база данни
1. Изберете тип база данни (например MySQL, PostgreSQL, MariaDB, Oracle, SQL Server)
2. Изберете версия на базата данни

#### 3. Конфигурирайте настройки на инстанцията
1. Изберете шаблон (например Production, Dev/Test, Free tier)
2. Въведете име на инстанцията
3. Изберете тип на инстанцията (например db.t2.micro за Free Tier)
4. Конфигурирайте съхранение (например General Purpose SSD)
5. Конфигурирайте настройки за Multi-AZ разполагане (опционално)
6. Конфигурирайте настройки за мрежа и сигурност (например VPC, subnet, security group)
7. Конфигурирайте настройки за идентификация и достъп (например потребителско име и парола за администратора)
8. Конфигурирайте допълнителни настройки (опционално):
   - **Backup** - автоматични резервни копия
   - **Monitoring** - CloudWatch мониторинг
   - **Maintenance** - автоматично пачване
   - **Encryption** - криптиране на данните
9. Кликнете "Create database"

### Управление на RDS инстанция

#### Свързване с базата данни
1. В RDS конзолата, изберете вашата инстанция
2. Кликнете "Connect"
3. Използвайте предоставената информация (endpoint, порт, потребителско име, парола) за връзка с базата данни чрез стандартни инструменти и библиотеки (например MySQL Workbench, pgAdmin, SQL Server Management Studio)

#### Изпълнение на SQL заявки
1. Свържете се с базата данни чрез предпочитания инструмент
2. Изпълнете SQL заявки за създаване на таблици, вмъкване на данни, актуализиране и изтриване на данни

#### Управление на сигурността
1. Конфигурирайте мрежова сигурност чрез VPC, subnet и security groups
2. Създайте потребители и роли с различни нива на достъп
3. Активирайте криптиране на данните (опционално)

#### Архивиране и възстановяване на данни
1. Конфигурирайте автоматични резервни копия в настройките на инстанцията
2. Създайте ръчни резервни копия чрез RDS конзолата
3. Възстановете данни от резервни копия при нужда

#### Мащабиране на ресурси
1. В RDS конзолата, изберете вашата инстанция
2. Кликнете "Modify"
3. Променете типа на инстанцията или капацитета на съхранение
4. Кликнете "Continue" и следвайте инструкциите за прилагане на промените

## Поддържани типове бази данни в RDS

Amazon RDS поддържа множество релационни бази данни, което ви позволява да изберете най-подходящата за вашето приложение.

### Основни типове бази данни:
1. **MySQL** - популярна отворена база данни с висока производителност и мащабируемост
2. **PostgreSQL** - мощна отворена база данни с поддръжка на разширени функции и разширения
3. **MariaDB** - форк на MySQL с допълнителни функции и оптимизации
4. **Oracle** - комерсиална база данни с поддръжка на разширени функции и висока производителност
5. **SQL Server** - комерсиална база данни от Microsoft с поддръжка на разширени функции и интеграция с други Microsoft продукти

### Избор на подходящ тип база данни
При избора на тип база данни, обмислете:
- **Изисквания на приложението** - специфични функции и разширения, необходими за вашето приложение
- **Производителност и мащабируемост** - способността на базата данни да се справя с натоварването
- **Съвместимост** - съвместимост с други компоненти на вашето приложение
- **Лицензиране и разходи** - разходи за лицензиране и поддръжка на базата данни

## Практически проект: Създаване на система за управление на потребители

В този проект ще създадем система за управление на потребители, използвайки Amazon RDS и други AWS услуги.

### Архитектура на проекта
1. Потребителят създава акаунт чрез уеб интерфейс
2. Данните за потребителя се записват в RDS база данни
3. Потребителят може да преглежда, актуализира и изтрива акаунта си

### Стъпка 1: Създаване на RDS инстанция
1. Създайте RDS инстанция с MySQL база данни
2. Изберете Free Tier опции (например db.t2.micro, 20 GB General Purpose SSD)
3. Конфигурирайте мрежова сигурност (VPC, subnet, security group)
4. Задайте потребителско име и парола за администратора

### Стъпка 2: Създаване на IAM роля за Lambda
1. Създайте IAM роля с следните разрешения:
   - `AWSLambdaBasicExecutionRole` - за CloudWatch Logs
   - `AmazonRDSFullAccess` - за достъп до RDS

### Стъпка 3: Създаване на Lambda функции

#### Функция за създаване на потребител (Node.js)
```javascript
const mysql = require('mysql');
const connection = mysql.createConnection({
    host: process.env.DB_HOST,
    user: process.env.DB_USER,
    password: process.env.DB_PASSWORD,
    database: process.env.DB_NAME
});

exports.handler = async (event) => {
    const { username, email, password } = JSON.parse(event.body);
    
    const query = 'INSERT INTO users (username, email, password) VALUES (?, ?, ?)';
    const values = [username, email, password];
    
    return new Promise((resolve, reject) => {
        connection.query(query, values, (error, results) => {
            if (error) {
                console.error('Error inserting user:', error);
                reject({
                    statusCode: 500,
                    body: JSON.stringify({ message: 'Error inserting user' })
                });
            } else {
                resolve({
                    statusCode: 201,
                    body: JSON.stringify({ message: 'User created', userId: results.insertId })
                });
            }
        });
    });
};
```

#### Функция за четене на потребители (Node.js)
```javascript
const mysql = require('mysql');
const connection = mysql.createConnection({
    host: process.env.DB_HOST,
    user: process.env.DB_USER,
    password: process.env.DB_PASSWORD,
    database: process.env.DB_NAME
});

exports.handler = async (event) => {
    const query = 'SELECT * FROM users';
    
    return new Promise((resolve, reject) => {
        connection.query(query, (error, results) => {
            if (error) {
                console.error('Error fetching users:', error);
                reject({
                    statusCode: 500,
                    body: JSON.stringify({ message: 'Error fetching users' })
                });
            } else {
                resolve({
                    statusCode: 200,
                    body: JSON.stringify(results)
                });
            }
        });
    });
};
```

#### Функция за актуализиране на потребител (Node.js)
```javascript
const mysql = require('mysql');
const connection = mysql.createConnection({
    host: process.env.DB_HOST,
    user: process.env.DB_USER,
    password: process.env.DB_PASSWORD,
    database: process.env.DB_NAME
});

exports.handler = async (event) => {
    const { userId, username, email, password } = JSON.parse(event.body);
    
    const query = 'UPDATE users SET username = ?, email = ?, password = ? WHERE id = ?';
    const values = [username, email, password, userId];
    
    return new Promise((resolve, reject) => {
        connection.query(query, values, (error, results) => {
            if (error) {
                console.error('Error updating user:', error);
                reject({
                    statusCode: 500,
                    body: JSON.stringify({ message: 'Error updating user' })
                });
            } else {
                resolve({
                    statusCode: 200,
                    body: JSON.stringify({ message: 'User updated' })
                });
            }
        });
    });
};
```

#### Функция за изтриване на потребител (Node.js)
```javascript
const mysql = require('mysql');
const connection = mysql.createConnection({
    host: process.env.DB_HOST,
    user: process.env.DB_USER,
    password: process.env.DB_PASSWORD,
    database: process.env.DB_NAME
});

exports.handler = async (event) => {
    const { userId } = JSON.parse(event.body);
    
    const query = 'DELETE FROM users WHERE id = ?';
    const values = [userId];
    
    return new Promise((resolve, reject) => {
        connection.query(query, values, (error, results) => {
            if (error) {
                console.error('Error deleting user:', error);
                reject({
                    statusCode: 500,
                    body: JSON.stringify({ message: 'Error deleting user' })
                });
            } else {
                resolve({
                    statusCode: 200,
                    body: JSON.stringify({ message: 'User deleted' })
                });
            }
        });
    });
};
```

### Стъпка 4: Пакетиране на Lambda функции
1. Създайте нова директория за всяка функция
2. Инициализирайте npm проект и инсталирайте зависимостите:
   ```bash
   mkdir create-user && cd create-user
   npm init -y
   npm install mysql
   # Създайте index.js с кода на функцията
   zip -r function.zip index.js node_modules
   ```

### Стъпка 5: Създаване на Lambda функции
1. Създайте Lambda функции за създаване, четене, актуализиране и изтриване на потребители
2. Качете ZIP файловете като код на функциите
3. Задайте `index.handler` като handler
4. Изберете създадената IAM роля
5. Увеличете timeout до 30 секунди и памет до 512 MB

### Стъпка 6: Създаване на API Gateway
1. Създайте нов REST API в API Gateway
2. Създайте ресурси и методи за създаване, четене, актуализиране и изтриване на потребители
3. Интегрирайте методите с Lambda функциите

### Стъпка 7: Тестване на системата
1. Използвайте Postman или друг инструмент за тестване на API
2. Създайте, прочетете, актуализирайте и изтрийте потребители чрез API
3. Проверете данните в RDS базата данни

## Допълнителни ресурси
- [Amazon RDS Documentation](https://docs.aws.amazon.com/rds/)
- [Amazon RDS Best Practices](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_BestPractices.html)
- [AWS Lambda Documentation](https://docs.aws.amazon.com/lambda/)
- [AWS API Gateway Documentation](https://docs.aws.amazon.com/apigateway/)
- [MySQL Documentation](https://dev.mysql.com/doc/)

## Въпроси за дискусия
1. Какви са предимствата и недостатъците на релационните бази данни спрямо NoSQL базите данни?
2. Как бихте избрали подходящ тип база данни за вашето приложение?
3. Какви мерки за сигурност бихте предприели за защита на данните в RDS?
