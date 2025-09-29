1. Моніторинг метрик EC2 в CloudWatch

Відкрити AWS CloudWatch → Metrics → EC2 → InstanceId.

- CPUUtilization (завантаження CPU)
- MemoryUtilization (завантаження пам’яті, якщо активовано CloudWatch Agent).

![cwa](images/graph1.png)

> Саме за вказаним шляхом `AWS CloudWatch → Metrics → EC2 → InstanceId` метрики відстуні, просте вони пристуні за `AWS CloudWatch → Metrics → CWAgent` 

2. Налаштування CloudWatch Alarms для CPU та пам’яті

Відкрити AWS CloudWatch → Alarms.

- CPU > 80% протягом 5 хвилин
- Memory > 75% протягом 5 хвилин

![alarms](images/alram-normal.png)

> Память я пізніше зменшив до 50% бо `streess` падає якщо задаєш більше ніж є free

3. Налаштування SNS-сповіщень

Відкрити Amazon SNS → Topics → Ваш топік.

- Створений SNS-топік
- Вказано вашу email-адресу
- Підтвердження підписки (Subscription confirmed)
![sns](images/sns.png)

4. Перевірка спрацювання аларму (створення навантаження)

Підключитися до EC2 через SSH

Виконати команду для створення навантаження:

`stress --cpu 2 --timeout 300`

![ssh](images/stress.png)
CloudWatch → Alarms, Alarm in ALARM state.

![alarm-red](images/alarm-red.png)



5. Отримане email-сповіщення про перевищення порогу


![email-cpu-first](images/alarm-cpu1.png)
![email-cpu-second](images/alarm-cpu2.png) 
![email-ram](images/alarm-ram.png)

> P.S. довго грався з RAM > 75%

6. Графік навантаження

Відкрити CloudWatch → Metrics → EC2 → CPUUtilization.


![graph](images/graph2.png)


7. Видалення ресурсів (якщо потрібно)

Відкрити AWS CloudWatch → Alarms → Delete.

![alarm-deleted](images/alarm-del.png)

Відкрити AWS CloudWatch → SNS → Delete topic.
![sns-deleted](images/sns-del.png)
