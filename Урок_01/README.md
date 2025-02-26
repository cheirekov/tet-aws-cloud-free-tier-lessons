# Урок 1: Въведение в AWS и Free Tier

## Цели на урока
- Да се запознаем с концепцията за облачни технологии
- Да разберем какво представлява Amazon Web Services (AWS)
- Да научим какво включва AWS Free Tier и как можем да го използваме

## Какво е облак и какви са предимствата му?

### Дефиниция на облачните технологии
Облачните технологии представляват модел за предоставяне на изчислителни ресурси (сървъри, съхранение, бази данни, мрежи, софтуер и др.) чрез интернет, обикновено на база "плащане според използването".

### Основни характеристики на облачните услуги:
- **Самообслужване при поискване** - потребителите могат сами да заявяват и управляват ресурси без човешка намеса от страна на доставчика
- **Широк мрежов достъп** - услугите са достъпни през мрежата чрез стандартни механизми
- **Обединяване на ресурси** - ресурсите на доставчика се обединяват, за да обслужват множество клиенти
- **Бърза еластичност** - ресурсите могат бързо да се увеличават или намаляват според нуждите
- **Измерима услуга** - използването на ресурси се следи, контролира и отчита

### Предимства на облачните технологии:
1. **Мащабируемост** – лесно разширяване или намаляване на ресурсите според нуждите
2. **Гъвкавост** – достъп от всяка точка на света с интернет връзка
3. **Намаляване на разходите** – плащане само за използваните ресурси, без нужда от големи първоначални инвестиции
4. **Надеждност** – облачните доставчици предлагат високо ниво на надеждност и резервираност
5. **Сигурност** – професионално управление на сигурността от експерти
6. **Автоматични актуализации** – софтуерът се актуализира автоматично от доставчика

### Модели на облачни услуги:
- **IaaS (Infrastructure as a Service)** - предоставя виртуални машини, мрежи, съхранение
- **PaaS (Platform as a Service)** - предоставя платформа за разработка и изпълнение на приложения
- **SaaS (Software as a Service)** - предоставя готов софтуер през интернет

## Кратък обзор на AWS и основните му услуги

### Какво е AWS?
Amazon Web Services (AWS) е водеща платформа за облачни услуги, предлагаща над 200 пълнофункционални услуги от центрове за данни по целия свят. AWS е създаден през 2006 г. и днес е най-големият доставчик на облачни услуги в света.

### Основни услуги на AWS:

#### Изчислителни услуги:
- **EC2 (Elastic Compute Cloud)** – виртуални сървъри в облака
- **Lambda** – безсървърно изпълнение на код
- **ECS/EKS** – управление на контейнери

#### Съхранение:
- **S3 (Simple Storage Service)** – съхранение на обекти
- **EBS (Elastic Block Store)** – блоково съхранение за EC2
- **Glacier** – архивно съхранение с ниска цена

#### Бази данни:
- **RDS (Relational Database Service)** – управлявани релационни бази данни
- **DynamoDB** – NoSQL база данни
- **ElastiCache** – кеширане в паметта

#### Мрежови услуги:
- **VPC (Virtual Private Cloud)** – изолирана мрежова среда
- **Route 53** – DNS услуга
- **CloudFront** – CDN (мрежа за доставка на съдържание)

#### Инструменти за разработка:
- **CodeCommit** – хранилище за код
- **CodeBuild** – компилиране и тестване на код
- **CodeDeploy** – автоматизирано разгръщане на код

#### Мониторинг и управление:
- **CloudWatch** – мониторинг на ресурси и приложения
- **CloudTrail** – проследяване на API активност
- **IAM (Identity and Access Management)** – управление на достъпа

## Какво включва AWS Free Tier?

AWS Free Tier позволява на нови потребители да използват безплатно определени AWS услуги в рамките на определени ограничения. Това е чудесен начин за запознаване с AWS без финансов риск.

### Категории на AWS Free Tier:

#### 1. Винаги безплатни услуги
Тези услуги нямат срок и са винаги безплатни в рамките на определени ограничения:
- **AWS Lambda** – 1 милион безплатни заявки месечно
- **Amazon DynamoDB** – 25 GB съхранение
- **Amazon CloudFront** – 1 TB изходящи данни месечно
- **Amazon CloudWatch** – 10 персонализирани метрики и аларми
- **AWS CodeBuild** – 100 минути време за изграждане месечно
- **AWS CodePipeline** – 1 активен pipeline месечно

#### 2. 12 месеца безплатни услуги
Тези услуги са безплатни за първите 12 месеца след създаване на AWS акаунт:
- **Amazon EC2** – 750 часа месечно на t2.micro или t3.micro инстанции
- **Amazon S3** – 5 GB стандартно съхранение
- **Amazon RDS** – 750 часа db.t2.micro или db.t3.micro инстанции, 20 GB съхранение
- **Amazon CloudFront** – 50 GB изходящи данни
- **Elastic Load Balancing** – 750 часа месечно

#### 3. Пробни услуги
Тези услуги предлагат краткосрочни безплатни пробни периоди:
- **Amazon SageMaker** – 250 часа месечно за 2 месеца
- **Amazon Redshift** – 750 часа месечно за 2 месеца
- **Amazon QuickSight** – 1 потребител безплатно за 30 дни

### Важни съображения при използване на AWS Free Tier:
- **Следете използването** – AWS предоставя инструменти за мониторинг на използването и разходите
- **Настройте аларми за таксуване** – създайте аларми, които да ви предупреждават, ако наближавате лимитите
- **Внимавайте с регионите** – някои услуги може да са безплатни само в определени региони
- **Не забравяйте да спирате ресурсите** – например, EC2 инстанциите продължават да се таксуват, дори когато са неактивни, ако не са спрени

## Практическа задача: Подготовка за създаване на AWS акаунт

### Какво ще ви трябва:
1. Валидна имейл адрес регистрация
2. Телефонен номер за верификация
3. Кредитна или дебитна карта (няма да бъде таксувана, ако останете в рамките на Free Tier)

### Стъпки за подготовка:
1. Проверете дали имейл адресът ви е достъпен и можете да получавате имейли
2. Уверете се, че телефонният ви номер може да получава SMS или обаждания за верификация
3. Проверете дали картата ви позволява международни транзакции (AWS може да направи малка верификационна транзакция, която след това се възстановява)

## Допълнителни ресурси
- [Официална страница на AWS Free Tier](https://aws.amazon.com/free/)
- [AWS Documentation](https://docs.aws.amazon.com/)
- [AWS Training and Certification](https://aws.amazon.com/training/)
- [AWS Architecture Center](https://aws.amazon.com/architecture/)

## Въпроси за дискусия
1. Какви са предимствата на облачните технологии спрямо традиционната инфраструктура?
2. Как бихте могли да използвате AWS Free Tier за лични или учебни проекти?
3. Какви типове приложения са подходящи за разработка с AWS Free Tier?
