# AndroidKursach

## План курсовой
- спроектировать систему
- бдшка
- экраны

### База данных 
Пользователи:
- айди
- пароль
- логин
- телефон/почта
- отпечаток пальца
- согласие с условиями
- имя (ФИО)
- face id

Карточки:
- айди
- номер
- айди аккаунта

Аккаунты:

Переводы:
- айди карточки
- айди получателя
- имя
- номер карты
- количество денег
- валюта
- комментарий
- сохранение
- комиссия
- otp (?)
- банк
- ветка банка

Сообщения:
- время отправки
- текст
- получатель

Счета

Настройки:
- язык
- информация о приложении (дата создания, версия)

### Функционал
- вход (вход, регистрация, восстановление пароля, вход по отпечатку пальца)
- изменение настроек (язык, изменение пароля, изменение данных о себе и отпечатка пальца)
- аккаунты (просмотр)

CREATE TABLE users(
	user_id serial PRIMARY KEY,
	user_first_name varchar(50) NOT NULL,
	user_middle_name varchar(50),
	user_last_name varchar(50) NOT NULL,
	password,
	login,
	email,
	phone,
	agreement,
	face_id,
	touch_id,
	user_photo
)

CREATE TABLE settings(
	settings_id,
	user_id,
	app_language,
	app_theme,
	app_version,
	installation_date
)

CREATE TABLE operations_history(
	operation_id,
	operation_type,
	operation_name,
	operation_date,
	additional_information,
	operation_status,
	sender,
	receiver
)

CREATE TABLE accounts(
	account_id,
	account_name,
	account_number,
	user_id,
	branch,
	balance
)

CREATE TABLE cards(
	card_id,
	account_id,
	card_number,
	bank_id,
	branch_id,
	owner_name,
	valid_from,
	good_thru
)

CREATE TABLE banks(
	bank_id,
	bank_name
)

CREATE TABLE cards_balance(
	balance_id,
	card_id,
	balance_amount
)

CREATE TABLE operation_statistics(
	operation_statistics_id,
	operation_type_id,
	operation_amount,
	card_id,
)

CREATE TABLE operation_types(
	operation_type_id,
	operation_type_name
)



CREATE TABLE bills(
	bill_id,
	bill_type_id,
	status_id,
	amount,
	date,
	name,
	address,
	phone_number,
	code,
	bill_from,
	bill_to,
	fee,
	tax
)

CREATE TABLE bill_payments(
	bill_payments_id,
	company,
	bill_code,
	bill_id,
	card_id,
	status,
	is_approved
)

CREATE TABLE deposits(

)

CREATE TABLE bill_types(
	bill_type_id,
	bill_type_name
)

CREATE TABLE transactions(
	transaction_id,
	transaction_type_id,
	card_id,
	receiver_account,
	bank_id,
	receiver_card_number,
	amount,
	content,
	is_saved,
	transaction_fee,
	is_approved,
	status_id,
	phone_number
)

CREATE TABLE transaction_types(
	transaction_type_id,
	transaction_type_name
)

CREATE TABLE notifications(
	notification_id,
	user_id,
	sending_time,
	notification_header,
	notification_text,
	notification_type_id
)

CREATE TABLE notification_type(
	notification_type_id,
	notification_type_name
)

-- динамические апи --

CREATE TABLE branches(
	branch_id,
	bank_id,
	branch_name,
	brach_address,
	branch_longitude,
	branch_latitude,
	working_hours
)

CREATE TABLE branch_status(
	branch_id,
	status_id
)

CREATE TABLE statuses(
	status_id,
	status_name
)

CREATE TABLE ratings(
	ratings_id,
	interest_kind,
	deposit,
	rate
)

CREATE TABLE exchange_rates(
	exchange_rate_id,
	country_id, 
	buy_value,
	sell_value
)

CREATE TABLE countries(
	country_id,
	country_name
)
- карточки
- смски пользователю
- перевод денег
- обмен валюты
