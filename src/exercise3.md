# Классификация

## 1. Тестирование форм

- ### Регистрация пользователя

    1. Пользователь уже есть в системе.  <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>
    2. Пользователя еще нет в системе.  <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
    3. Проверка полей на валидацию. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>

- ### Авторизация пользователя

    1. Пользователь существует в системе с введенным логином и паролем. <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
    2. Пользователь с введенным логином не существует в системе. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>
    3. Пользователь с введенным логином существует в системе, но пароль неверный. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>
    4. Валидация полей ввода. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>
    5. Восстановление пароля существующего пользователя. <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
    6. Восстановление пароля несуществующего пользователя. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>

- ### Предложение продуктов

    1. Валидация полей ввода. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>
    2. Добавление нового продукта. <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
    3. Добавление продукта в новый банк. <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
    4. Добавление неавторизованным пользователем. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>
    

- ### Создание банка

    1. Валидация полей ввода. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>
    2. Некорректный ввод. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>
    3. Корректный ввод. <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
    4. Создание банка не администратором. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>

## 2. Тестирование поиска по продуктам и банкам

1. Результаты существуют/не существуют. <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
2. Пустой поисковой запрос. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>
3. Сортировка. <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
4. Фильтры с выдачей. <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
5. Фильтры без выдачи. <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>

## 3. Тестирование профиля пользователя

1. Удаление аккаунта <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
2. Редактирование профиля <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
3. Редактирование профиля с изменением пароля <mark>*Позитивное*</mark> <span style="background-color: black">Чёрный ящик</span>
4. Редактирование профиля с вводом некорректных данных <span style="background-color: red">Негативное</span> <span style="background-color: black">Чёрный ящик</span>

## 4. Тестирование API
1. Регистрация через API <mark>*Позитивное*</mark> <span style="background-color: grey">Серый ящик</span>
2. Авторизация <mark>*Позитивное*</mark> <span style="background-color: grey">Серый ящик</span>
3. Создание банка <mark>*Позитивное*</mark> <span style="background-color: grey">Серый ящик</span>
4. Получение списка ролей <mark>*Позитивное*</mark> <span style="background-color: grey">Серый ящик</span>
5. Регистрация пользователя <mark>*Позитивное*</mark> <span style="background-color: grey">Серый ящик</span>
6. Регистрация работника банка <mark>*Позитивное*</mark> <span style="background-color: grey">Серый ящик</span>