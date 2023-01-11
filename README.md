# Need_Game - система рекомендаций игр.

**Цель исследования - ответить на вопросы и построить рекомендательную систему.**

**Вопросы:**
1. На какой платформе вышло больше всего игр?
2. Сколько эксклюзивных игр вышло от разных платформодержателей?
3. У какой компании самые высокооцененные игры?
4. Какие самые высокооцененные игры в каждой компании?

**Ход исследования**

Перед решением задачи понадобится обзор данных. Затем на этапе предобработки данных исправим найденные ошибки. На этапе исследования данных дадим ответы на вопросы. Затем посчитаем матрицу косинуса схожести по описанию игр.


# Выводы

Для проведения исследования доступны данные 19837 игр.

На этапе предобработки данных мы заменили значения `tbd` в колонке `userscore` на оценки критиков делённые на 10 и изменили тип данных на `float64`, изменили тип колонки `date` на `datetime`, удалили пропуски в колонке `summary` и удалили дубликаты игр. В таблице осталось 12749 строки.

**Анализ данных показал:**

1. В период с 1996 по 2022 годах на платформу от компании Sony вышло больше всего игр (6057). Немного отстает от первого места персональный компьютер (5214). В 2008 и 2018 наблюдается 2 пиковых значения по количеству выходимых игр и последующие спады. Незадолго до этого выходили консоли нового поколения. Можно предположить, что новые проекты создаются и выпускаются в начале и середине жизненного цикла платформы. Далее уже разрабатываются игры под новое поколения.

2. В период с 1996 по 2022 годах на консоли Nintendo вышло больше всего эксклюзивных игр (2749) и в тоже время меньше всего мультиплатформенных игр. Связано это с тем, что Nintendo выпускает слабые консоли относительно конкурентов и разработчикам сложно портировать свои игры. Компания Sony на втором месте с результатом 2439. Меньше всех, из большой тройки, вышло эксклюзивов на консоли от Microsoft (945).

3. Игры от компании Nintendo обладают самой высокой оценкой от критиков (69.17) и игроков (7.15). Компания Sony совсем немного отстает от первого места (69.06 и 7.1). У Microsoft оценки сильно хуже в сравнении с конкурентами (65.74 и 6.69). Начиная с 1996 средний бал от игроков показывает отрицательную линейную связь, то есть с каждым годом падаю.

4. Самые высокооцененные игры: 
    - у компании Nintendo по версии критиков это `The Legend of Zelda: Ocarina of Time` с оценкой 99, по версии игроков `Ghost Trick: Phantom Detective` с оценкой 9.7
    - у компании Sony по версии критиков это `Tekken 3`, `Gran Turismo`, `Metal Gear Solid 2: Sons of Liberty` и `Uncharted 2: Among Thieves` с оценкой 96, по версии игроков `Z.H.P. Unlosing Ranger vs Darkdeath Evilman` с оценкой 9.7
    - у компании Microsoft по версии критиков это `Grand Theft Auto Double Pack` с оценкой 96, по версии игроков `NieR: Automata - Become as Gods Edition` с оценкой 9.1


На основе данных мы посчитали меру сходства игр и сохранили в файл `cosine_similarity.pkl`.  

Для построения рекомендательной системы возьмем гармоническое среднее от меры сходства, оценки от критиков и игроков (предварительно нормализовав их). 

Эта система может быть полезна для поиска похожих игр.

**Попробывать можно в [телеграм боте](https://t.me/need_game_bot).**

# Стек
`pandas`, `matplotlib`, `numpy`, `sklearn`, `requests`, `psycopg2`, `difflib`, `telegram`