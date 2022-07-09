# WBL0

## Тестовое задание:

#### В БД:
1. Развернуть локально postgresql
2. Создать свою бд
3. Настроить своего пользователя.
4. Создать таблицы для хранения полученных данных.

#### В сервисе:
1. Подключение и подписка на канал в nats-streaming
2. Полученные данные писать в Postgres
3. Так же полученные данные сохранить in memory в сервисе (Кеш)
4. В случае падения сервиса восстанавливать Кеш из Postgres
5. Поднять http сервер и выдавать данные по id из кеша
6. Сделать простейший интерфейс отображения полученных данных, для их запроса по id

#### Доп инфо:
1. Данные статичны, исходя из этого подумайте насчет модели хранения в Кеше и в pg. Модель в файле model.json
2. В канал могут закинуть что угодно, подумайте как избежать проблем из-за этого
3. Чтобы проверить работает ли подписка онлайн, сделайте себе отдельный скрипт, для публикации данных в канал
4. Подумайте как не терять данные в случае ошибок или проблем с сервисом
5. Nats-streaming разверните локально ( не путать с Nats )

#### Бонус задание
1. Покройте сервис автотестами. Будет плюсик вам в карму
2. Устройте вашему сервису стресс тест, выясните на что он способен -
воспользуйтесь утилитами WRK, Vegeta. Попробуйте оптимизировать код

### Пример json
```
{
  "order_uid": "b563feb7b2b84b6test",
  "track_number": "WBILMTESTTRACK",
  "entry": "WBIL",
  "delivery": {
    "name": "Test Testov",
    "phone": "+9720000000",
    "zip": "2639809",
    "city": "Kiryat Mozkin",
    "address": "Ploshad Mira 15",
    "region": "Kraiot",
    "email": "test@gmail.com"
  },
  "payment": {
    "transaction": "b563feb7b2b84b6test",
    "request_id": "",
    "currency": "USD",
    "provider": "wbpay",
    "amount": 1817,
    "payment_dt": 1637907727,
    "bank": "alpha",
    "delivery_cost": 1500,
    "goods_total": 317,
    "custom_fee": 0
  },
  "items": [
    {
      "chrt_id": 9934930,
      "track_number": "WBILMTESTTRACK",
      "price": 453,
      "rid": "ab4219087a764ae0btest",
      "name": "Mascaras",
      "sale": 30,
      "size": "0",
      "total_price": 317,
      "nm_id": 2389212,
      "brand": "Vivienne Sabo",
      "status": 202
    }
  ],
  "locale": "en",
  "internal_signature": "",
  "customer_id": "test",
  "delivery_service": "meest",
  "shardkey": "9",
  "sm_id": 99,
  "date_created": "2021-11-26T06:22:19Z",
  "oof_shard": "1"
}
```
