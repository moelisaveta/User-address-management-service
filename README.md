<h1 align="center">Сервис управления адресами пользователей</h1>  

## 1. Бизнес-требование

Разработать и внедрить функционал управление адресами пользователей в мобильное приложение и веб-платформу сервиса, позволяющее пользователям добавлять новые адреса, получать списов всех сохраненных адресов, а также обновлять существующие данных об адресах. Это позволит пользователям упростить процесс и сократить временя оформления заказа.

## 2. Глоссарий
| Понятие  | Определение |
| ------------- | ------------- |
| Адрес  | Набор данных, представляющий конкретное местоположение, включая такие поля, как улица, дом, квартира, город, область, почтовый индекс и странам |
| Добавление адреса  | Процесс внесения нового адреса в систему, который может включать заполнение необходимых полей и сохранение данных |
| Интерфейс пользователя (UI) | Визуальная часть сервиса, с помощью которой пользователи взаимодействуют с системой, включая элементы управления для добавления, обновления и получения адресов |
| Обновление адреса | Процесс изменения существующих данных об адресе. Пользователь может вносить исправления или добавлять дополнительную информацию |
| Подтверждение | Сообщение, получаемое пользователем после успешного выполнения операции с адресом, подтверждающее успешность добавления, обновления или удаления |
| Получение списка адресов| Функция, позволяющая пользователю запрашивать и получать полный список всех адресов, сохраненных в системе |
| Пользователь  | Лицо, которое имеет доступ к сервису и взаимодействует  с функционалом |
| Удаление адреса | Процесс удаления адреса из системы. Пользователь может удалить адрес, который больше не нужен |

## 3. Контекст требований
**Проблема:**

Пользователи нуждаются в удобном и интуитивно понятном инструменте для добавления, обновления и получения информации об адресах.
Необходимо решить:
- <b>Отсутствие централизованного решения:</b> На текущий момент отсутствуют эффективные решения для управления адресами, которые могли бы поддерживать взаимодействие пользователей с данными.
- <b>Сложность обновления данных:</b> При необходимости изменить адрес, пользователи могут забыть или не знать, где именно хранится информация. Это может привести к ошибкам в доставке.
- <b>Отсутствие надежной валидации адресов:</b> Ошибки при вводе адресов (например, опечатки или некорректные форматы) могут привести к дополнительным затратам и задержкам.

## 4. Цель разработки
**Зачем мы это делаем?**

**Что это дает бизнесу?**

## 5. Функциональрные требования

## 6. Нефункциональные требование

## 7. Техническое задание
**User store**

**1. Добавление нового адреса**

- Как: Пользователь приложения
- Я хочу: Иметь возможность добавлять адреса
- Чтобы: Для быстрого выбора нужного адреса

**Acceptance Criteria:**
- [ ] Пользователь находится на вкладке добавления нового адреса с отображением карты
- [ ] Пользователь нажимает на кнопку "Ввести новый адрес", вводит адрес и сохраняет его
- [ ] Система сохраняет адрес и отображает пользователю введенный адрес, время доставки и кнопки "Да, все верно" и "Ввести другой адрес"
- [ ] Пользователь подтверждает адрес
- [ ] Пользователь получает уведомление об успешном добавлении адреса

## BPMN
![TOBE](https://raw.githubusercontent.com/moelisaveta/User-address-management-service/a7066a82692eb004311de1343cf26e8ab792013a/bpmn_1.png)

### Frontend
  - Добавить в приложение новую вкладку с разделом "Адреса" согласно текущему дизайну приложения.
  - Добавить кнопку "Адреса" в интерфейс главной страницы личного кабинета пользователя. Использовать кнопку согласно дизайну приложения (ссылка на дизайн).
  - При нажатии на "Адреса" отображается кнопка "Новый адрес" согласно дизайну приложения (ссылка на дизайн) и список всех сохраненных пользователем адресов (описано далее). Отправляется запрос GET на бэкенд для получения списка сохранённых адресов.
  - При нажатии на кнопку "Новый адрес" отобразить пользователю лоудер "Загружаем карту..." (ссылка на дизайн) до момента получения ответа от сервера.
  - Отобразить карту 2GIS с отображением текущего местоположения и кнопки "Да, все верно" и "Ввести другой адрес" согласно дизайну приложения (ссылка на дизайн).
  - При нажатии на кнопку "Ввести другой адрес"  отобразить форму для добавления нового адреса: Реализовать форму для ввода данных адреса, включая элементы для выбора компонентов "Город" (текстовое поле) и "Улица и дом" (текстовое поле).
  - После заполнения формы  и нажатия на кнопку "Да, всё верно" отправить запрос POST на бэкенд.
     - В случае если адрес некорректен оповестить пользователя сообщением "Ничего не нашли. Проверьте адрес".
     - В случае, если местоположение, определенное на карте, не обслуживается доставкой, отобразить пользователю сообщение "Сюда доставить не можем" и добавить кнопку "Ввести адрес" согласно дизайну приложения (ссылка на дизайн). Аналогично п. 7  отобразить форму для добавления нового адреса и  отправить запрос POST на бэкенд.
  - В случае успешно введенного с карты/вручную адреса отобразить время доставки и нажатии на кнопку "Да, все верно", вернуть пользователя на главную страницу личного кабинета пользователя.


