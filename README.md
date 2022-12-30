# Manual System Testing

Привет, студент Школы 21! Этот проект — первая часть курса по технологиям и методикам контроля качества программного обеспечения, Quality Assurance — QA. Как следует из названия, QA — это не только и не столько тестирование, будь то ручное или автоматизированное, это набор методик и подходов, предназначенных для выявления и контроля всех несоответствий качества программных продуктов. Начнём наше знакомство здесь и сейчас с тестирования: первым делом познакомим тебя с основными терминами и понятиями тестирования, тестовыми артефактами, техниками тест-дизайна, а также узнаем, что такое баг-репорты и как их правильно оформлять.

## Contents

1. [Chapter I](#chapter-i) \
    1.1. [Определение и цели](#определение-и-цели) \
    1.2. [Классификация](#классификация) \
    1.3. [Уровни тестирования](#уровни-тестирования) \
    1.4. [Задание №1](#задание-№1-тестирование-в-разработке) \
    1.5. [Функциональность](#функциональность) \
    1.6. [Задание №2](#задание-№2-список-тестовых-сценариев) \
    1.7. [Позитивность](#позитивность) \
    1.8. [Знания о системе](#знания-о-системе) \
    1.9. [Степень автоматизации](#степень-автоматизации) \
    1.10. [Особые виды тестирования](#особые-виды-тестирования) \
    1.11. [Задание №3](#задание-№3-классификация-тестовых-сценариев)
2. [Chapter II](#chapter-ii) \
    2.1. [Тестовые артефакты](#тестовые-артефакты) \
    2.2. [Тест-кейс](#тест-кейс) \
    2.3. [Чек-лист](#чек-лист) \
    2.4. [Задание №4](#задание-№4-создание-чек-листов) \
    2.5. [Тест-план](#тест-план) \
    2.6. [Баг-репорт](#баг-репорт) \
    2.7. [Задание №5](#задание-№5-составление-баг-репортов)
3. [Chapter III](#chapter-iii) \
    3.1. [Тест-дизайн](#тест-дизайн) \
    3.2. [Классы эквивалентности](#классы-эквивалентности) \
    3.3. [Граничные значения](#граничные-значения) \
    3.4. [Попарное тестирование](#попарное-тестирование) \
    3.5. [Сценарии использования](#сценарии-использования) \
    3.6. [Интуитивное тестирование](#интуитивное-тестирование) \
    3.7. [Задание №6](#задание-№6-обновление-чек-листов)

## Chapter I

### Определение и цели

Тестирование — это процесс оценки программного продукта на предмет его соответствия поставленным требованиям.

Зачем проводится тестирование? Попробуем сформулировать это так:

- чтобы повысить вероятность того, что приложение, предназначенное для тестирования, будет работать правильно при любых обстоятельствах;
- чтобы повысить вероятность того, что приложение, предназначенное для тестирования, будет соответствовать всем описанным требованиям;
- чтобы иметь предоставление актуальной информации о состоянии продукта на данный момент;
- чтобы выявить ситуации, в которых поведение программы является не правильным или не соответствующим спецификации.

### Классификация

Существует множество оснований, по которым можно классифицировать виды тестирования ПО — уровень, функциональность, позитивность и другие. Рассмотрим их на схеме:

![types](misc/images/types.png)

И познакомимся же подробнее с некоторыми!

### Уровни тестирования

Существуют четыре уровня тестирования:

- **Модульное** (оно же компонентное) **тестирование** — проверка функциональности тех частей ПО (мы также будем использовать термины _система_, _программа_, _программное обеспечение_ здесь и далее по курсу — не пугайся!), которые можно протестировать отдельно, в изоляции от общей системы;
- **Интеграционное тестирование** — проверка интеграции подсистем в общую систему, их взаимодействия между собой. В рамках интеграционного тестирования используются компоненты, ранее проверенные с помощью модульного тестирования;
- **Системное тестирование** — тестирование ПО на полной, интегрированной системе, с целью проверки этой системы на соответствие требованиям, как функциональным, так и нефункциональным;
- **Приемочное тестирование** — тестирование, проводимое при сдаче продукта заказчику. Целью приемочного тестирования является определение готовности программного продукта к использованию конечными пользователями. Набор тест-кейсов и сценариев разрабатывается на основании требований к данному приложению.

Эти уровни тестирования (помимо специфического **приемочного**) подробно рассматриваются в данном курсе.

### **Задание №1. Тестирование в разработке**

Создай файл `exercise1.md` в папке `src`. А теперь, пользуясь своими навыками проектирования и разработки программных продуктов, а также дополнительными материалами, опиши в этом файле: каким образом, на каких стадиях жизненного цикла, кем и в каком составе может проводиться каждый из этих уровней тестирования. Озаглавь свои идеи как `# Уровни тестирования`.

### Функциональность

Тестирование можно разделить на **функциональное** и **нефункциональное**. Основная задача функционального тестирования — подтверждение того, что разрабатываемый программный продукт обладает всем функционалом, требуемым заказчиком или продукт-овнером. Соответственно, задачей нефункционального тестирования является проверка свойств, не относящихся к функциональности системы.

Нефункциональное тестирование проверяет 6 основных свойств:

- Надежность (реакция системы на внештатные ситуации);
- Производительность (работоспособность системы при различных нагрузках);
- Удобство (удобство работы с ПО с перспективы пользователя);
- Масштабируемость (возможность горизонтального или вертикального масштабирования приложения);
- Безопасность (защищенность данных);
- Портируемость (переносимость ПО на различные платформы).

### **Задание №2. Список тестовых сценариев**

В файле `materials/object.md` представлена инструкция по доступу к нашему **объекту тестирования** и его **краткое описание**. Это реальное приложение, разработанное реальными разработчиками, слепок которого в промежуточном виде был специально для каждого из вас размещён на отдельном [веб-сервере](http://10.101.255.2:4200) 🤗. Зайди по указанной инструкции в приложение — и постарайся описать своими словами в файле `src/exercise2.md` (создай этот файл!) список сценариев функционального тестирования так, чтобы они были как можно более исчерпывающими для проверки всего заявленного функционала. Помести этот список под заголовок `# Список тестовых сценариев`.

### Позитивность

Тестирование делят на **позитивное** и **негативное**.

**Позитивное тестирование** подразумевает проверку системы с помощью сценариев, соответствующих её _ожидаемому_ поведению. С его помощью проверяется, что система делает то, для чего была создана.

В **негативном тестировании** используются сценарии, соответствующие _внештатному_ поведению программы, то есть мы проверяем наше приложение на заведомо неверных входных данных, которые могли бы вызвать сбои. Негативное тестирование считается пройденным лишь в том случае, если подобные тест-кейсы не вызывают никаких сбоев в приложении.

### Полнота знаний

По полноте знаний о системе тестирование можно разделить на 3 вида: **"белый ящик"**, **"серый ящик"** и **"черный ящик"**.

#### **Белый ящик**

Дадим определение.

**"Белым ящиком"** называется метод тестирования программного обеспечения, который предполагает, что внутренняя структура системы известна тестировщику. Входные значения выбираются, основываясь на знании кода, который будет их обрабатывать. Аналогично, мы знаем, каким должен быть результат этой обработки. Знание всех особенностей тестируемой программы и ее реализации обязательны для этого подхода. Тестирование белого ящика основано на углублении во внутреннее устройство системы.

#### **Черный ящик**

Несложно догадаться, что **"чёрным ящиком"** называется метод тестирования, напротив, основанный на работе только с внешними интерфейсами системы, без какой-либо информации о ее внутреннем устройстве.

#### **Серый ящик**

Также по аналогии отметим, что это метод тестирования ПО с неполным знанием его внутреннего устройства. Например, у нас может быть доступ к интерфейсам классов, но не их реализации.

### Степень автоматизации

По степени автоматизации тестирование можно разбить на 3 типа:

- **Автоматическое** — тестирование проводится специальным тестирующим ПО, написанным ранее;
- **Ручное** — тестирование проводится вручную человеком-тестером;
- **Полуавтоматическое** — части процесса тестирования выполняются тестирующим ПО, но оно не способно провести весь цикл тестирования без участия человека-тестера;

В рамках нашего курса мы познакомимся с каждым из этих трёх видов, но начнём, разумеется, с ручного тестирования.

### Особые виды тестирования

Существуют еще несколько видов тестирования, не попадающие ни под одну из описанных выше категорий, но которые стоит упомянуть.

**Тестирование документации** — проверка документации на полноту, удобство навигации, наличие инструкций, наличие определений терминов, доступность пользователю.

**"Дымовое" тестирование**: короткий цикл тестов, выполняемый для подтверждения того, что после сборки кода устанавливаемое приложение стартует и выполняет основные функции.

**Регрессионное тестирование**: проверка изменений, сделанных в приложении или окружающей среде (починка дефекта, слияние кода, миграция на другую операционную систему, базу данных, веб сервер или сервер приложения), для подтверждения того факта, что существующая ранее функциональность работает как и прежде. Регрессионными могут быть как функциональные, так и нефункциональные тесты.

### **Задание №3. Классификация тестовых сценариев**

Теперь постарайся классифицировать свои тестовые сценарии, описанные тобой в предыдущем задании, по критерию позитивности и полноте знаний. Свои результаты добавь в файл `src/exercise3.md` под заголовком `## Классификация`.

## Chapter II

### Тестовые артефакты

В процессе тестирования ПО используется ряд **тестовых артефактов**. Рассмотрим наиболее распространенные из них.

**Баг-репорт** — документ, описывающий несоответствие реальной работы программы с предъявленными к ней требованиями.

**Тест-кейс** — последовательность действий, по которой можно проверить, соответствует ли тестируемая функция установленным требованиям.

**Тест-план** — документ, который описывает весь объем работ по тестированию, начиная с описания объекта, стратегии, расписания, критериев начала и окончания тестирования, до необходимого в процессе работы оборудования, специальных знаний, а также оценки рисков с вариантами их разрешения.

**Чек-лист** — набор тест-кейсов.

В этой части мы познакомимся с каждым из них подробнее!

### Тест-кейс

**Тест-кейс** — это тестовый артефакт, суть которого заключается в выполнении некоторого количества действий и условий, необходимых для проверки определенного функционала разрабатываемого ПО.

Из чего состоит тест-кейс? Типичную структуру можно представить вот так:

- ID кейса
- Заголовок
- Шаги
- Ожидаемый результат
- Предшествующие условия

Пример:

![testcase_ex](misc/images/testcase_ex.png)

_Следует избегать ситуации, когда один тест-кейс зависит от другого, и может быть проверен только после него!_

Стоит также выделить понятие **тестовое покрытие** или же просто **покрытие**. Дадим ему определение.

**Тестовое покрытие** — одна из метрик оценки качества тестирования, представляющая из себя плотность покрытия тестами требований, либо исполняемого кода.

**Покрытие требований** — оценка покрытия тестами функциональных и нефункциональных требований к продукту путем построения матриц трассировки.

**Матрица покрытия функционала**, или **матрица трассировки** – это двумерная таблица, содержащая соответствие функциональных требований продукта и подготовленных тестовых сценариев. Пример такой матрицы:

![traceability_matrix](misc/images/traceability_matrix.png)

Расчет тестового покрытия относительно требований проводится по формуле: `Tcov = (Lcov/ Ltotal) * 100%`, где: `Tcov` — тестовое покрытие, `Lcov` — количество требований, проверяемых тест-кейсами, `Ltotal` — общее количество требований. В реальной разработке очень важно обеспечить покрытие требований, близкое к 100%, однако случаи, когда кто-то будет действительно высчитывать процент, достаточно редки 🤪.

В процессе разработки тест-кейсов необходимо следить за тестовым покрытием. Набор тестов к ПО должен быть **необходимым и достаточным** для обеспечения требуемого уровня покрытия. Проще говоря, всегда требуется составить минимально возможный набор тестов, который будет покрывать весь функционал ПО.

### Чек-лист

**Чек-лист** — документ, описывающий, что именно должно быть протестировано. Чаще всего (что даже видно из названия) представляет собой последовательность шагов. Уж с чем-чем, а с чек-листами ты хорошо знаком, верно?

Чек-лист может быть абсолютно разного уровня детализации. Детальность чек-листа зависит от требований к отчётности, уровня знания продукта сотрудниками и сложности продукта, а также количества времени, которое было выделено на тестирование.

Чек-лист имеет 2 ключевых плюса:

- История тестов — можно выделить те из них, что были провалены, и перепроверить только их.
- Наглядность — легко оценить состояние продукта и стадию проверок.

Из минусов стоит выделить низкий уровень детализации в конкретных реализациях и отсутствие подробного документирования, что может стать проблемой для новых сотрудников.

### **Задание №4. Создание чек-листов**

На основании полученных теоретических знаний и дополнительных материалов оформи каждый сценарий, проработанный в предыдущих заданиях, как тест-кейс (вероятно, тебе придётся его декомпозировать!), и составь из них чек-лист. После этого проведи тестирование веб-приложения по своему чек-листу. Помести результаты прогона чек-листа в каждый соответствующий раздел файла `src/exercise4.md` и опиши своими словами, что же пошло не так (если пошло!).

### Тест-план

**Тест-план** — документ, описывающий весь объем работ по тестированию, начиная с описания тестируемых объектов, стратегии, расписания, критериев начала и окончания тестирования, до необходимого в процессе работы оборудования, специальных знаний, а также оценки рисков с вариантами их разрешения.

Плюсы:

- Возможность приоритизации задач по тестированию.
- Построение стратегии тестирования, согласованной со всей командой.
- Возможность вести учет всех требуемых ресурсов, как технических, так и человеческих.
- Планирование использования ресурсов на тестирование.
- Просчет рисков, возможных при проведении тестирования.

Несмотря на этот ряд преимуществ, тест-план _применим далеко не всегда_. Чтобы в его составлении был смысл, на тестирование и разработку ПО должно быть выделено неограниченное (или просто очень большое) количество времени, так как его создание, во-первых, занимает много времени само по себе, а, во-вторых, подразумевает возможность назначения сроков, удобных команде QA, в то время как в действительности основное время приоритетно разработчикам.

### Баг-репорт

**Баг-репорт** описывает найденный дефект. В связи с этим актуален вопрос "Что вообще является багом?". Объективного ответа на этот вопрос, как правило, нет. При решении этого вопроса в первую очередь стоит проверить требования к ПО. Если проверка требований, имеющейся базы знаний или технического задания не дала четкого ответа на вопрос, следует подумать о баге с перспективы пользовательского опыта: если пользователю может показаться что данное поведение системы — ошибка... скорее всего, так оно и есть.

Из чего состоит (должен состоять) баг-репорт?

- Заголовок
- Предшествующие условия
- Приоритетность
- Шаги воспроизведения
- Фактический результат
- Ожидаемый результат
- Окружение

**Заголовок** — краткое описание сути бага. Заголовок следует писать, основываясь на принципе **"Что? Где? Когда?"**.

**Что?** — Что происходит/не происходит согласно документации/представлению о
нормальной работе продукта.

**Где?** — В каком элементе ПО возникает дефект.

**Когда?** — При каких действиях возникает дефект.

При написании заголовка стоит избегать слов "Плохо", "Неправильно" и похожих, так как они неточно описывают суть проблемы. Иначе есть риск, что разработчики, читая такое описание бага, _отправят что-то чувствительное в зрительный зал_... 😏

Шаги для воспроизведения должны быть **четко и подробно** описаны. Их задача — перечислить все действия, необходимые, чтобы повторить баг, они дожны быть понятны не только пишущему их человеку, но и любому другому читателю баг-репорта.

**Приоритет** — срочность, с которой необходимо исправить баг. Обычно выделяют **Blocker, Critical, Major, Minor & Trivial** приоритеты багов, а также **Backlog** в случае, если решение проблемы будет отложено "в долгий ящик". Приоритет определяется в зависимости от **серьёзности** — степени влияния бага на систему.

Посмотрим на пример репорта:

```
Заголовок:
Краш приложения при смене языка на арабский в настройках языка

Предшествующие условия:
Пользователь авторизован в приложении.

Шаги для воспроизведения:

1. Открыть меню настроек
2. Зайти в настройки языка
3. Изменить язык на арабский

Ожидаемый результат:
Язык текста в приложении меняется на арабский

Фактический результат:
Приложение падает с ошибкой, отображается сообщение об ошибке.

Окружение:
Версия 1.0, IPhone4/IOS 9.1
```

Также по возможности к баг-репорту следует приложить видео, скриншоты, логи, дампы дистрибутивов и любые другие относящиеся к багу материалы.

Важно помнить и знать о принципе **"Один дефект — один репорт"**. Если на проблему уже заведен баг-репорт, второй заводить не нужно, это только создаст замешательство о количестве багов в системе. С другой стороны, если багов несколько, даже если они возникают в одном и том же окне и имеют общие черты, не стоит пытаться описать их всех одним репортом, лучше завести по репорту на каждый.

### **Задание №5. Составление баг-репортов**

Опиши все найденные тобой на предыдущих шагах проблемы в формате баг-репортов. **Используй для этого доску задач репозитория GitLab**. Убедись, что каждый дефект был оформлен надлежащим образом. Если вдруг тебе покажется, что дефектов в приложении нет... тебе лишь кажется — и лучше ещё раз тщательно пройтись по предыдущим заданиям.

*P.S.: Перейдя по [этой ссылке](https://docs.gitlab.com/ee/user/project/issues/managing_issues.html), можно познакомиться с GitLab Issues*

## Chapter III

### Тест-дизайн

**Тест-дизайн** – это этап процесса тестирования ПО, на котором проектируются и создаются тест-кейсы в соответствии с определёнными ранее критериями качества и целями тестирования.

**Тест-дизайнер** – это сотрудник, в чьи обязанности входит создание тест-кейсов, обеспечивающих оптимальное тестовое покрытие тестируемого продукта.

Существует целый ряд техник тест-дизайна. Среди основных можно выделить следующие:

- Классы эквивалентности
- Граничные значения
- Попарное тестирование
- Сценарии использования
- Интуитивное тестирование

Рассмотрим их поподробнее.

### Классы эквивалентности

**Класс эквивалентности** — одно или несколько значений ввода, к которым программное обеспечение применяет одинаковую логику.

Техника анализа классов эквивалентности заключается в том, что мы разделяем функционал (часто разделяется множество возможных входных значений) на группы эквивалентных по своему влиянию на систему частей. Такое разделение помогает убедиться в правильном функционировании целой системы — одного класса эквивалентности, — проверив только один элемент этой группы. Эта техника заключается в разбиении всего набора тестов на классы эквивалентности с целью дальнейшего сокращения количества тестов.

### Граничные значения

**Граничные значения** — это значения, в которых один класс эквивалентности переходит в другой.

Техника граничных значений является идейным продолжением и развитием техники эквивалентных классов, и применима только в комбинации с ней. Согласно технике граничных значений, помимо проверки значений из середины класса, надо проверять значения на границах.

### Попарное тестирование

**Попарное тестирование** — техника тест-дизайна, которая обеспечивает полное тестовое покрытие.

ISTQB определяет попарное тестирование как технику тест-дизайна методом черного ящика, при которой тест-кейсы создаются таким образом, чтобы выполнить все возможные отдельные комбинации каждой пары входных параметров.

Основная идея данной техники заключается в том, что при большом количестве и высокой вариативности параметров, проверить все возможные их комбинации слишком время- и трудозатратно. При попарном тестировании предполагается, что если в процессе тестирования были проверены все комбинации для каждой отдельно взятой пары параметров, то полученное покрытие эквивалентно таковому при полном переборе значений всех возможных комбинаций всех параметров.

### Сценарии использования

**Сценарии использования** (Use-case, зачастую — юскейсы) описывают сценарии взаимодействия двух и более участников (как правило – пользователя и системы). Пользователем может выступать как человек, так и другая система. Для специалистов QA Use Case являются отличной базой для формирования тестовых сценариев (тест-кейсов), так как они описывают, в каком контексте должно производиться каждое действие пользователя. Use Case, по умолчанию, являются проверяемыми требованиями, так как в них всегда указана цель, которую нужно достигнуть, и шаги, которые надо для этого воспроизвести.

### Интуитивное тестирование

**Интуитивное тестирование** — вид тестирования, который выполняется без подготовки к тестам, без определения ожидаемых результатов, проектирования тестовых сценариев. Это неформальное, импровизационное тестирование. Оно не требует никакой документации, планирования, процессов, которых следует придерживаться в выполнении. Также на данный вид тестирования не пишутся тест-кейсы, что в свою очередь может вызвать определенные затруднения в попытках воспроизвести дефект в системе. Такой вид зачастую может дать сходу больше результатов, чем тестирование по заранее определенным сценариям. Это обусловлено тем, что тестировщик на первых шагах приступает к тестированию основного функционала и выполняет нестандартные проверки, точнее некоторые из его проверок будут нестандартными.

### **Задание №6. Обновление чек-листов**

На основании освоенных материалов главы разбей тест-кейсы на классы эквивалентности и выдели граничные значения. Опиши, когда и какие техники из перечисленных ты использовал при классификации тест-кейсов. Обнови предыдущий чек-лист новыми тест-кейсами. Помести новые материалы в `src/exercise6.md` (создай файл на основе своего предыдущего!) и проведи тестирование полученным чек-листом вновь.

_________________________________________

Поздравляем! Первый шаг к мастерству Quality Assurance сделан. Ещё многое впереди, но кое-чему ты уже научился 😉

А ещё мы подготовили для тебя список дополнительной литературы, который позволит тебе лучше освоиться в материале этого и последующих блоков:
- Святослав Куликов — "Тестирование программного обеспечения. Базовый курс. (3-е издание)"
- Роман Савин — "Тестирование Дот Ком"    
- Гленфорд Майерс — "Искусство тестирования программ"
- [Ham Vocke — The Practical Test Pyramid](https://martinfowler.com/articles/practical-test-pyramid.html)
- [Martin Fowler — TestPyramid](https://martinfowler.com/bliki/TestPyramid.html)

Какие существуют стандарты? Ниже мы описали некоторые из широко используемых стандартов, связанных с обеспечением качества и тестированием:
- **ISO / IEC 9126** (рассматриваются различные аспекты для определения качества программного приложения)
- **ISO / IEC 9241-11** (рассматривается степень, в которой продукт может использоваться указанными пользователями для достижения определенных целей)
- **ISO / IEC 25000: 2005** (рекомендации по требованиям и оценке качества программного обеспечения — _SQuaRE_)
- **ISO / IEC 12119** (о пакетах программного обеспечения, поставляемых клиенту)
- **IEEE 829** (стандарт для формата документов, используемых на разных этапах тестирования программного обеспечения)
- **IEEE 1008** (стандарт для модульного тестирования)
- **IEEE 1059** (руководство по планам проверки и валидации программного обеспечения)
- **IEEE 1061** (методология определения требований к качеству, метрики)
- **BS 7925-1** (словарь терминов, используемых при тестировании программного обеспечения)
- **BS 7925-2** (стандарт для тестирования компонентов программного обеспечения)

Пожалуйста, оставь обратную связь по проекту в [форме обратной связи](https://forms.gle/xBtc6hukjJ7qgy8Y7).
