1. Моніторинг метрик EC2 в CloudWatch

Відкрити AWS CloudWatch → Metrics → EC2 → InstanceId.

Зробити скрин, де видно:

CPUUtilization (завантаження CPU)
MemoryUtilization (завантаження пам’яті, якщо активовано CloudWatch Agent).


2. Налаштування CloudWatch Alarms для CPU та пам’яті

Відкрити AWS CloudWatch → Alarms.

Зробити скрин з налаштованими алармами:

CPU > 80% протягом 5 хвилин,
Memory > 75% протягом 5 хвилин.


3. Налаштування SNS-сповіщень

Відкрити Amazon SNS → Topics → Ваш топік.

Зробити скрин, де видно:

Створений SNS-топік
Вказано вашу email-адресу
Підтвердження підписки (Subscription confirmed)




4. Перевірка спрацювання аларму (створення навантаження)

Підключитися до EC2 через SSH

Виконати команду для створення навантаження:

stress --cpu 2 --timeout 300

 або

yes > /dev/null &

Зробити скрин CloudWatch → Alarms, де видно Alarm in ALARM state.



5. Отримане email-сповіщення про перевищення порогу

Зробити скрин повідомлення в електронній пошті, яке надійшло після спрацювання аларму.



6. Графік навантаження

Відкрити CloudWatch → Metrics → EC2 → CPUUtilization.

Зробити скрин, де видно зріст навантаження під час тесту.



7. Видалення ресурсів (якщо потрібно)

Відкрити AWS CloudWatch → Alarms → Delete.

Відкрити AWS CloudWatch → SNS → Delete topic.

Зробити скрин, що аларми та SNS-топік видалені.

