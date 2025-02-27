# Урок 1: Основи на облачните изчисления

## Въведение
Този урок обхваща основните концепции и модели на разгръщане в облачните изчисления. Ще разгледаме ползите от използването на облачни технологии и как те могат да трансформират бизнеса.

## Концепции и модели на разгръщане

### Публичен облак
- **Описание**: Услугите се предоставят чрез интернет и са достъпни за всички.
- **Примери**: AWS, Microsoft Azure, Google Cloud Platform.
- **Предимства**: Гъвкавост, мащабируемост, икономия на разходи.

### Частен облак
- **Описание**: Облакът е предназначен за използване от една организация.
- **Управление**: Може да се управлява вътрешно или от трета страна.
- **Предимства**: Повишена сигурност и контрол.

### Хибриден облак
- **Описание**: Комбинация от публични и частни облаци.
- **Употреба**: Позволява данни и приложения да се споделят между различни среди.
- **Предимства**: Гъвкавост и оптимизация на разходите.

## Ползи от облачните технологии
- **Гъвкавост**: Лесно мащабиране на ресурси според нуждите.
- **Икономия на разходи**: Плащане само за използваните ресурси.
- **Достъпност**: Достъп до услуги от всяка точка на света.
- **Бързина**: Бързо внедряване на нови услуги и приложения.

## Заключение
Разбирането на основите на облачните изчисления е критично за всеки, който иска да работи с AWS. Тези концепции формират основата на всички облачни услуги и решения.

## Допълнителни ресурси
- [AWS Cloud Computing Basics](https://aws.amazon.com/what-is-cloud-computing/)
- [Introduction to Cloud Computing on AWS](https://aws.amazon.com/training/)


# Урок 2: AWS Global Infrastructure

## Въведение
В този урок ще разгледаме глобалната инфраструктура на AWS, включително региони, зони на наличност и точки на присъствие. Тези елементи са ключови за разбирането на това как AWS предоставя надеждни и мащабируеми услуги.

## Региони и зони на наличност

### Региони
- **Описание**: Географски области, състоящи се от две или повече зони на наличност.
- **Предимства**: Възможност за избор на регион, близък до клиентите за по-ниска латентност.
- **Примери**: US East (N. Virginia), EU (Frankfurt), Asia Pacific (Tokyo).

### Зони на наличност
- **Описание**: Изолирани локации в рамките на регион, които предлагат висока достъпност.
- **Предимства**: Защита от сривове в отделни зони.

## Точки на присъствие

### Edge Locations
- **Описание**: Местоположения за кеширане на съдържание, които подобряват доставката на данни до крайните потребители.
- **Употреба**: Използват се от услуги като Amazon CloudFront за по-бързо доставяне на съдържание.

## Заключение
AWS Global Infrastructure е основата, върху която се изграждат всички услуги на AWS. Разбирането на тази инфраструктура е критично за проектирането на надеждни и мащабируеми решения.

## Допълнителни ресурси
- [AWS Global Infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)
- [Regions and Availability Zones](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html)


# Урок 3: Основни AWS услуги

## Въведение
Този урок ще ви запознае с основните AWS услуги, които са критични за разбирането и използването на AWS. Ще разгледаме EC2, S3, RDS, VPC и IAM.

## EC2 (Elastic Compute Cloud)
- **Описание**: Виртуални сървъри в облака, които могат да бъдат конфигурирани според нуждите.
- **Употреба**: Хостване на приложения, уеб сървъри, бази данни.
- **Функции**: Автоматично мащабиране, различни типове инстанции.

## S3 (Simple Storage Service)
- **Описание**: Обектно съхранение за данни с висока издръжливост и достъпност.
- **Употреба**: Архивиране, съхранение на медийни файлове, хостване на статични уебсайтове.
- **Функции**: Версиониране, политики за достъп, криптиране.

## RDS (Relational Database Service)
- **Описание**: Управлявани релационни бази данни, които автоматизират задачи като архивиране и мащабиране.
- **Употреба**: Хостване на релационни бази данни като MySQL, PostgreSQL, Oracle.
- **Функции**: Автоматично архивиране, репликация, мониторинг.

## VPC (Virtual Private Cloud)
- **Описание**: Изолирани мрежови среди, които позволяват контрол върху мрежовите настройки.
- **Употреба**: Създаване на сигурни мрежови архитектури.
- **Функции**: Подмрежи, маршрути, интернет шлюзове.

## IAM (Identity and Access Management)
- **Описание**: Управление на достъпа и идентичностите в AWS.
- **Употреба**: Контрол на достъпа до ресурси чрез потребители, групи и роли.
- **Функции**: Политики за достъп, MFA, роли за услуги.

## Заключение
Основните AWS услуги са в основата на много облачни решения. Разбирането на тези услуги е критично за всеки, който иска да работи като "Облачен инженер"


## Примери за платформи и приложения, хоствани на AWS

AWS е предпочитан избор за много големи компании и платформи поради своята надеждност, мащабируемост и широка гама от услуги. Ето някои известни примери:

### Netflix
- **Описание**: Netflix използва AWS за стрийминг на своето съдържание към милиони потребители по целия свят. AWS предоставя инфраструктурата, необходима за обработка на големи обеми от данни и осигуряване на непрекъснато предаване на видео.

### Airbnb
- **Описание**: Airbnb използва AWS за хостване на своята платформа, която свързва милиони домакини и гости. AWS помага на Airbnb да мащабира своите операции и да обработва големи обеми от транзакции и данни.

### Slack
- **Описание**: Slack, популярната платформа за бизнес комуникация, използва AWS за своите сървъри и инфраструктура. AWS осигурява надеждност и сигурност, необходими за поддържане на комуникацията в реално време.

### Pinterest
- **Описание**: Pinterest използва AWS за съхранение и обработка на милиарди изображения и данни от потребителите. AWS позволява на Pinterest да мащабира своите услуги според нуждите на потребителите.

### Spotify
- **Описание**: Spotify използва AWS за хостване на своята музикална платформа, която предоставя стрийминг на музика на милиони потребители. AWS осигурява инфраструктурата, необходима за обработка на големи обеми от аудио данни и персонализирани препоръки.

### Twitch
- **Описание**: Twitch, платформата за стрийминг на видео игри, използва AWS за своите сървъри и инфраструктура. AWS осигурява мащабируемост и надеждност, необходими за предаване на видео в реално време към милиони зрители.

Тези примери демонстрират как AWS може да поддържа големи и сложни платформи, предоставяйки им необходимата гъвкавост и мащабируемост за успех в глобален мащаб.

## Tаблица предоставяща по-подробен преглед на услугите, предлагани от AWS, Azure, GCP и Alibaba Cloud. Въпреки това, всяка платформа предлага множество други услуги и функционалности, които не са включени тук. Препоръчвам да посетите официалните сайтове на доставчиците за най-актуалната и подробна информация.

| Услуга | AWS | Azure | GCP | Alibaba Cloud |
|--------|-----|-------|-----|--------------|
| **Изчислителни услуги** |
| Виртуални машини | EC2 (Elastic Compute Cloud) | Virtual Machines | Compute Engine | ECS (Elastic Compute Service) |
| Контейнери | ECS (Elastic Container Service), EKS (Elastic Kubernetes Service) | AKS (Azure Kubernetes Service) | GKE (Google Kubernetes Engine), Anthos | ACK (Alibaba Container Service for Kubernetes) |
| Безсървърни изчисления | Lambda | Functions | Cloud Functions | Function Compute |
| **Бази данни** |
| Релационни бази данни | RDS (Relational Database Service) | SQL Database | Cloud SQL | RDS (Relational Database Service) |
| NoSQL бази данни | DynamoDB | Cosmos DB | Firestore, Bigtable | ApsaraDB for MongoDB, Redis, etc. |
| Кеширане | ElastiCache | Redis Cache | Memorystore | ApsaraDB for Redis |
| **Съхранение** |
| Обектно съхранение | S3 (Simple Storage Service) | Blob Storage | Cloud Storage | OSS (Object Storage Service) |
| Блок съхранение | EBS (Elastic Block Store) | Managed Disks | Persistent Disk | ESSD (Elastic SSD) |
| Архивиране | Glacier | Archive Storage | Coldline Storage | Object Storage Service (OSS) Archive |
| **Мрежови услуги** |
| Виртуални частни мрежи (VPC) | VPC | Virtual Network | VPC | VPC (Virtual Private Cloud) |
| Балансиране на натоварването | ELB (Elastic Load Balancer) | Load Balancer | Load Balancing | SLB (Server Load Balancer) |
| CDN (Content Delivery Network) | CloudFront | CDN | Cloud CDN | Content Delivery Network (CDN) |
| **Сигурност** |
| Идентичност и достъп | IAM (Identity and Access Management) | Azure AD | IAM & IAP | RAM (Resource Access Management) |
| Защита от DDoS атаки | Shield | DDoS Protection Plan | DDoS Protection | Anti-DDoS Premium |
| Криптиране | KMS (Key Management Service) | Key Vault | Cloud KMS | KMS (Key Management Service) |
| **Анализ и машинно обучение** |
| Анализ на големи данни | EMR (Elastic MapReduce), Redshift | HDInsight, Data Lake Analytics | Dataproc, BigQuery | MaxCompute |
| Машинно обучение | SageMaker | Machine Learning Studio | AI Platform, AutoML | PAI (Platform for Artificial Intelligence) |
| **Управление и мониторинг** |
| Мониторинг | CloudWatch | Monitor | Stackdriver | ARMS (Application Realtime Monitoring Service) |
| Лог мениджмънт | CloudTrail, CloudWatch Logs | Log Analytics | Logging, Error Reporting | SLS (Log Service) |
| Оркестрация и автоматизация | CloudFormation | Resource Manager | Deployment Manager | CloudFormation, Resource Orchestration Service (ROS) |
| **Интеграция и API управление** |
| API Gateway | API Gateway, AppSync | API Management | Apigee API Platform | API Gateway |
| **Интернет на нещата (IoT)** |
| IoT услуги | IoT Core, Greengrass | IoT Hub, IoT Central | Cloud IoT Core | IoT Platform |
| **Бизнес приложения** |
| Работни пространства | WorkSpaces, Chime | Dynamics 365, Power BI | Looker, Google Workspace | DingTalk, EnterpriseDing |
| **Мобилни услуги** |
| Мобилни разработки | Amplify, Pinpoint | Mobile Apps, Notification Hubs | Firebase | Mobile Push, Mobile Analytics |
| **DevOps и CI/CD** |
| DevOps инструменти | CodePipeline, CodeBuild | DevOps, Pipelines | Cloud Build, Spinnaker | CodePipeline, DevOps Pro |
| **Гейминг** |
| Гейминг услуги | GameLift | PlayFab | Game Servers | Game Server |
| **Медийни услуги** |
| Медийни решения | MediaConvert, Elemental | Media Services | Media CDN, Video AI | VOD (Video on Demand), Live Streaming |
| **Киберсигурност** |
| Киберсигурност | GuardDuty, Inspector | Security Center, Sentinel | Chronicle, BeyondCorp | WAF (Web Application Firewall), CASB (Cloud Access Security Broker) |
| **Блокчейн** |
| Блокчейн услуги | Managed Blockchain | Azure Blockchain Service | Blockchain Nodes | BaaS (Blockchain as a Service) |

