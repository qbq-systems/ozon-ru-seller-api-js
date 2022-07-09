# v1/actions

### GET

Метод для получения списка акций, которые доступны для партнёра

<u>api</u>   

```
API.v1.actions.get()
```   

# v1/actions/candidates

### POST

Метод для получения списка товаров по идентификатору акции, которые могут в ней участвовать

<u>body</u>   

* action_id {double} Идентификатор акции   
* limit {int64} Количество значений в ответе   
* offset {int64} Количество элементов, которое будет пропущено в ответе.   

<u>api</u>   

```
API.v1.actions.candidates.get(
    action_id: DoubleType,
    offset: Int64Type,
    limit: Int64Type = 100,
)
```   

# v1/actions/products

### POST

Метод для получения списка товаров по идентификатору акции, которые в ней участвуют

<u>body</u>   

* action_id {double} Идентификатор акции   
* limit {int64} Количество значений в ответе   
* offset {int64} Количество элементов, которое будет пропущено в ответе.   

<u>api</u>   

```
API.v1.actions.products.get(
    action_id: DoubleType,
    offset: Int64Type,
    limit: Int64Type = 100,
)
```   

# v1/actions/products/activate

### POST

Метод для добавления товаров в доступную для партнёра акцию

<u>body</u>   

* action_id {double} Идентификатор акции   
* products {array}    

<u>api</u>   

```
API.v1.actions.products.activate.addProductsToAction(
    action_id: DoubleType,
    products: ProductType|ProductType[],
)
```   

# v1/actions/products/deactivate

### POST

<u>body</u>   

* action_id {double} Идентификатор акции   
* product_ids {array} Список идентификаторов товаров   

<u>api</u>   

```
API.v1.actions.products.deactivate.deleteProductsFromAction(
    action_id: DoubleType,
    product_ids: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v1/analytics/data

### POST

Уĸажите период и метриĸи, ĸоторые нужно посчитать — в ответе будет аналитиĸа, сгруппированная по параметру dimensions.

<u>body</u>   

* date_from {dateFull}    
* date_to {dateFull}    
* dimension {arrayOfEnum} Группировка данных в отчёте   
* filter {array} Фильтры   
* limit {int64} Количество значений в ответе   
* metrics {arrayOfEnum} Укажите до 14 метрик.   
* offset {int64} Количество элементов, которое будет пропущено в ответе.   
* sort {array} Настройки сортировки отчёта.   

<u>api</u>   

```
API.v1.analytics.data.get(
    date_from: DateFullType,
    date_to: DateFullType,
    dimension: ArrayOfEnumType,
    filter: DefaultItemNameType|DefaultItemNameType[],
    metrics: ArrayOfEnumType,
    offset: Int64Type,
    sort: DefaultItemNameType|DefaultItemNameType[],
    limit: Int64Type = 100,
)
```   

# v1/analytics/item_turnover

### POST

Метод для получения отчёта по оборачиваемости (FBO) по категориям за последние 15 дней.

<u>body</u>   

* date_from {dateFull}    

<u>api</u>   

```
API.v1.analytics.item_turnover.get(
    date_from: DateFullType,
)
```   

# v1/analytics/stock_on_warehouses

### POST

Отчёт по остаткам и товарам в перемещении по складам Ozon.

<u>body</u>   

* limit {int64} Количество значений в ответе   
* offset {int64} Количество элементов, которое будет пропущено в ответе.   

<u>api</u>   

```
API.v1.analytics.stock_on_warehouses.get(
    offset: Int64Type,
    limit: Int64Type = 100,
)
```   

# v1/brand/company-certification/list

### POST

Метод для получения списка брендов, для которых требуется предоставить сертификат

Ответ содержит список брендов, товары которых есть в вашем личном кабинете. Список брендов может изменяться, если Ozon получит требование от бренда предоставлять сертификат.

<u>body</u>   

* page {int32} Номер страницы, возвращаемой в запросе   
* page_size {int32} Количество элементов на странице   

<u>api</u>   

```
API.v1.brand.company-certification.list.get(
    page: Int32Type,
    page_size: Int32Type,
)
```   

# v1/categories/tree

### GET

Дерево нескольких категорий товаров

Возвращает категории для товаров в виде дерева. Создание товаров доступно только в категориях последнего уровня, сравните именно эти категории с категориями своей площадки. Категории не создаются по запросу пользователя.

<u>query</u>   

* category_id {int64} Идентификатор категории   
* language {enum} Язык в ответе   

<u>api</u>   

```
API.v1.categories.tree.get(
    category_id: Int64Type,
    language: EnumType = DEFAULT,
)
```   

# v1/chat/history

### POST

Возвращает историю сообщений в чате.

По умолчанию сообщения показываются от старого к новому. Чтобы получить историю сообщений от самого нового сообщения до самого старого, используйте метод /v1/chat/updates. У методов /v1/chat/history и /v1/chat/updates одинаковая структура запроса и ответа.

<u>body</u>   

* chat_id {string} Идентификатор чата.   
* from_message_id {uint64} Идентификатор сообщения, с которого начать вывод истории чата.   
* limit {int64} Количество значений в ответе   

<u>api</u>   

```
API.v1.chat.history.get(
    chat_id: StringType,
    from_message_id: Uint64Type,
    limit: Int64Type = 100,
)
```   

# v1/chat/list

### POST

Возвращает информацию о чатах с указанными идентификаторами.

В ответе метода могут быть чаты с last_message_id = 0 и без сообщений. Это происходит, когда покупатель открыл чат с продавцом, но ничего не написал.

<u>body</u>   

* chat_list_id {array} Массив с идентификаторами чатов, для которых нужно вывести информацию.   
* page {int32} Количество страниц в ответе.   
* page_size {int32} Количество чатов на странице.   
* with {object}    

<u>api</u>   

```
API.v1.chat.list.get(
    chat_list_id: DefaultItemNameType|DefaultItemNameType[],
    page: Int32Type,
    withArg: ObjectType,
    page_size: Int32Type = 100,
)
```   

# v1/chat/send/file

### POST

Отправляет файл в существующий чат по его идентификатору.

<u>body</u>   

* chat_id {string} Идентификатор чата.   
* base64_content {string} Файл в виде строки base64.   
* name {string} Название файла с расширением.   

<u>api</u>   

```
API.v1.chat.send.file.post(
    chat_id: StringType,
    base64_content: StringType,
    name: StringType,
)
```   

# v1/chat/send/message

### POST

Отправляет сообщение в существующий чат по его идентификатору.

<u>body</u>   

* chat_id {string} Идентификатор чата.   
* text {string} Текст сообщения в формате plain text.   

<u>api</u>   

```
API.v1.chat.send.message.send(
    chat_id: StringType,
    text: StringType,
)
```   

# v1/chat/start

### POST

Создает новый чат с покупателем по отправлению.

Например, чтобы уточнить адрес или модель товара.

<u>body</u>   

* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v1.chat.start.create(
    posting_number: StringType,
)
```   

# v1/chat/updates

### POST

<u>body</u>   

* chat_id {string} Идентификатор чата.   
* from_message_id {uint64} Идентификатор сообщения.   
* limit {int64} Количество значений в ответе   

<u>api</u>   

```
API.v1.chat.updates.get(
    chat_id: StringType,
    from_message_id: Uint64Type,
    limit: Int64Type = 100,
)
```   

# v1/delivery-method/list

### POST

<u>body</u>   

* filter {object} Фильтр для поиска методов доставки   
* limit {int64} Количество значений в ответе   
* offset {int64} Количество элементов, которое будет пропущено в ответе.   

<u>api</u>   

```
API.v1.delivery-method.list.get(
    filter: ObjectType,
    offset: Int64Type,
    limit: Int64Type = 100,
)
```   

# v1/polygon/bind

### POST

<u>body</u>   

* delivery_method_id {array} Идентификатор способа доставки.   
* polygons {array}    
* warehouse_location {object}    

<u>api</u>   

```
API.v1.polygon.bind.create(
    delivery_method_id: DefaultItemNameType|DefaultItemNameType[],
    polygons: PolygonType|PolygonType[],
    warehouse_location: ObjectType,
)
```   

# v1/polygon/create

### POST

Вы можете добавить полигон к методу доставки

Создайте полигон, получив его координаты на https://geojson.io: отметьте на карте минимум 3 точки и соедините их линиями.

<u>body</u>   

* coordinates {array}    

<u>api</u>   

```
API.v1.polygon.create.post(
    coordinates: PolygonType|PolygonType[],
)
```   

# v1/polygon/delete

### POST

<u>body</u>   

* polygon_ids {array} Список идентификаторов полигонов   

<u>api</u>   

```
API.v1.polygon.delete.remove(
    polygon_ids: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v1/posting/carriage-available/list

### POST

Метод для получения перевозок, для которых нужно распечатать акт приёма-передачи и транспортную накладную.

<u>body</u>   

* delivery_method_id {array} Идентификатор способа доставки.   
* departure_date {dateTimeTz} Дата отгрузки.   

<u>api</u>   

```
API.v1.posting.carriage-available.list.get(
    delivery_method_id: DefaultItemNameType|DefaultItemNameType[],
    departure_date: DateTimeTzType,
)
```   

# v1/product/archive

### POST

<u>body</u>   

* product_id {array}    

<u>api</u>   

```
API.v1.product.archive.moveToArchive(
    product_id: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v1/product/import/info

### POST

Узнать статус добавления товара

<u>body</u>   

* id {int64} Номер задания   

<u>api</u>   

```
API.v1.product.import.info.getStatus(
    id: Int64Type,
)
```   

# v1/product/import/prices

### POST

Позволяет изменить цену одного или нескольких товаров

За один запрос можно изменить цены для 1000 товаров. Чтобы сбросить old_price или premium_price — поставьте 0 у этих параметров. Новая цена должна отличаться от старой минимум на 5%.

<u>body</u>   

* prices {array}    

<u>api</u>   

```
API.v1.product.import.prices.update(
    prices: PriceType|PriceType[],
)
```   

# v1/product/import/stocks

### POST

Позволяет изменить информацию о количестве товара в наличии

Метод используется только для FBS и rFBS складов. Метод используется только для FBS и rFBS складов. Задать наличие товара возможно только после того, как его статус сменится на processed.

<u>body</u>   

* stocks {array}    

<u>api</u>   

```
API.v1.product.import.stocks.get(
    stocks: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v1/product/import-by-sku

### POST

Создаёт товар по указанному Ozon ID

Количество товаров не ограничено.

<u>body</u>   

* items {array}    

<u>api</u>   

```
API.v1.product.import-by-sku.create(
    items: ItemType|ItemType[],
)
```   

# v1/product/info/description

### POST

<u>body</u>   

* offer_id {string} Идентификатор товара в системе продавца — артикул   
* product_id {int64} Идентификатор товара   

<u>api</u>   

```
API.v1.product.info.description.get(
    offer_id: StringType,
    product_id: Int64Type,
)
```   

# v1/product/info/stocks-by-warehouse/fbs

### POST

<u>body</u>   

* fbs_sku {array}    

<u>api</u>   

```
API.v1.product.info.stocks-by-warehouse.fbs.get(
    fbs_sku: SkuType|SkuType[],
)
```   

# v1/product/pictures/import

### POST

Метод для загрузки или обновления изображений товара

Например, если вы вызвали метод и загрузили 10 изображений, а затем вызвали метод второй раз и загрузили ещё одно, то все 10 предыдущих сотрутся.

<u>body</u>   

* color_image {string} Маркетинговый цвет   
* images {array} Массив изображений   
* images360 {array} Массив изображений 360   
* product_id {int64} Идентификатор товара   

<u>api</u>   

```
API.v1.product.pictures.import.updateImages(
    color_image: StringType,
    images: ImageUrlType|ImageUrlType[],
    images360: Image360UrlType|Image360UrlType[],
    product_id: Int64Type,
)
```   

# v1/product/pictures/info

### POST

<u>body</u>   

* product_id {array} Список идентификаторов товаров   

<u>api</u>   

```
API.v1.product.pictures.info.getStatus(
    product_id: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v1/product/certificate/accordance-types

### GET

<u>api</u>   

```
API.v1.product.certificate.accordance-types.get()
```   

# v1/product/certificate/bind

### POST

<u>body</u>   

* certificate_id {int64} Идентификатор сертификата, который был присвоен при его загрузке   
* product_id {array} Массив идентификаторов товаров, к которым относится этот сертификат   

<u>api</u>   

```
API.v1.product.certificate.bind.create(
    certificate_id: Int64Type,
    product_id: ProductIdType|ProductIdType[],
)
```   

# v1/product/certificate/create

### POST

<u>body</u>   

* files {array} Массив сертификатов для товара   
* name {string} Название сертификата   
* number {string} Номер сертификата   
* type_code {enum} Тип сертификата   
* accordance_type_code {enum} Тип соответствия требованиям   
* issue_date {dateTimeTz} Дата начала действия сертификата   
* expire_date {dateTimeTz} Дата окончания действия сертификата   

<u>api</u>   

```
API.v1.product.certificate.create.upload(
    files: FileType|FileType[],
    name: StringType,
    number: StringType,
    type_code: EnumType,
    accordance_type_code: EnumType,
    expire_date: DateTimeTzType,
    issue_date: DateTimeTzType = 2021-04-30T11:31:26Z,
)
```   

# v1/product/certificate/types

### GET

<u>api</u>   

```
API.v1.product.certificate.types.get()
```   

# v1/product/certification/list

### POST

<u>body</u>   

* page {int32} Номер страницы, возвращаемой в запросе   
* page_size {int32} Количество элементов на странице   

<u>api</u>   

```
API.v1.product.certification.list.get(
    page: Int32Type,
    page_size: Int32Type,
)
```   

# v1/product/unarchive

### POST

<u>body</u>   

* product_id {array}    

<u>api</u>   

```
API.v1.product.unarchive.restoreFromArchive(
    product_id: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v1/product/upload_digital_codes

### POST

Загрузите коды активации, если вы загружаете цифровые товары или услуги. Код активации привязывается к карточке цифрового товара.

<u>body</u>   

* digital_codes {array} Цифровые коды активации   
* product_id {int64} Идентификатор товара   

<u>api</u>   

```
API.v1.product.upload_digital_codes.update(
    digital_codes: DefaultItemNameType|DefaultItemNameType[],
    product_id: Int64Type,
)
```   

# v1/product/upload_digital_codes/info

### POST

Метод для получения статуса загрузки кодов активации для услуг и цифровых товаров.

<u>body</u>   

* id {int64} Номер задания   

<u>api</u>   

```
API.v1.product.upload_digital_codes.info.get(
    id: Int64Type,
)
```   

# v1/products/geo-restrictions-catalog-by-filter

### POST

<u>body</u>   

* filter {object} Фильтр   
* last_order_number {int64} Порядок геоограничения, с которого выводим данные в ответе   
* limit {int64} Количество значений в ответе   

<u>api</u>   

```
API.v1.products.geo-restrictions-catalog-by-filter.get(
    filter: ObjectType,
    last_order_number: Int64Type,
    limit: Int64Type = 100,
)
```   

# v1/report/finance/create

### POST

Отчёт по финансам за выбранный период с информацией о балансе на начало и конец периода.

Отчёт содержит: * сумма, полученная за доставленные заказы; * сумма комиссии за доставленные заказы; * сумма за возвращённые товары; * сумма, возвращённая за возвраты, * сумма оплаты за услуги.

<u>body</u>   

* date_from {dateFull}    
* date_to {dateFull}    
* language {enum} Язык в ответе   

<u>api</u>   

```
API.v1.report.finance.create.create(
    date_from: DateFullType,
    date_to: DateFullType,
    language: EnumType = DEFAULT,
)
```   

# v1/report/info

### POST

Возвращает информацию о созданном ранее отчёте по его идентификатору.

<u>body</u>   

* code {string} Уникальный идентификатор отчёта.   

<u>api</u>   

```
API.v1.report.info.get(
    code: StringType,
)
```   

# v1/report/list

### POST

Возвращает список отчётов, которые были сформированы раньше.

<u>body</u>   

* page {int32} Количество страниц в ответе.   
* page_size {int32} Количество заказов на странице   
* report_type {enum} Тип отчёта   

<u>api</u>   

```
API.v1.report.list.get(
    page: Int32Type,
    page_size: Int32Type = 100,
    report_type: EnumType = ALL,
)
```   

# v1/report/postings/create

### POST

<u>body</u>   

* language {enum} Язык в ответе   
* filter {object}    

<u>api</u>   

```
API.v1.report.postings.create.create(
    filter: ObjectType,
    language: EnumType = DEFAULT,
)
```   

# v1/report/product/create

### POST

Метод для получения отчёта с данными о товарах.

Пояснения к некоторым полям: Ozon Product ID — идентификатор товара в нашей системе. Например, если вы продаёте товар со склада Ozon и со своего склада, Ozon Product ID будет для них одинаковым. * FBO Ozon SKU ID — идентификатор товара, который продаётся со склада Ozon. * FBS Ozon SKU ID — идентификатор товара, который продаётся с вашего склада. * CrossBorder Ozon SKU — идентификатор товара, который продаётся из-за границы. * Barcode — штрихкод товара, который печатается на маркировке. * Статус товара — можно ли купить товар на Ozon. Если статус «Готов к продаже», товар купить нельзя. * Доступно на складе Ozon, шт — сколько штук товара на складе доступно для продажи. Это количество не включает зарезервированные товары. * Зарезервировано, шт — сколько штук товара со статусом «Зарезервировано». Товар зарезервирован с момента получения заказа на Ozon и до упаковки для передачи покупателю. * Текущая цена с учётом скидки, руб. — цена, по которой товар продаётся сейчас (на момент загрузки отчёта, с учётом скидки). Если на товар участвует в акции, указана цена без её учёта. * Базовая цена (цена до скидок), руб. — цена без учёта скидки. * Цена Premium, руб. — цена для покупателей с подпиской Ozon Premium. * Рекомендованная цена, руб. — минимальная цена на товар на другой торговой площадке. * Актуальная ссылка на рекомендованную цену — ссылка на товар с рекомендованной ценой на другой торговой площадке.

<u>body</u>   

* language {enum} Язык в ответе   
* offer_id {array} Идентификатор товара в системе продавца.   
* search {string} Поиск по содержанию записи, проверяет наличие.   
* sku {int64} Идентификатор товара в системе Ozon — SKU   
* visibility {enum} Фильтр по видимости товара   

<u>api</u>   

```
API.v1.report.product.create.create(
    offer_id: DefaultItemNameType|DefaultItemNameType[],
    search: StringType,
    sku: Int64Type,
    language: EnumType = DEFAULT,
    visibility: EnumType = ALL,
)
```   

# v1/report/products/movements/create

### POST

Отчёт с полной информацией по товарам, а также количество единиц товара со статусами: * товары с браком или на инвентаризации, * товары в перемещении между фулфилмент-центрами, * товары в доставке, * товары, подлежащие реализации.

<u>body</u>   

* date_from {dateTimeTz}    
* date_to {dateTimeTz}    
* language {enum} Язык в ответе   

<u>api</u>   

```
API.v1.report.products.movements.create.create(
    date_from: DateTimeTzType,
    date_to: DateTimeTzType,
    language: EnumType = DEFAULT,
)
```   

# v1/report/products/prices/create

### POST

<u>body</u>   

* language {enum} Язык в ответе   
* offer_id {string} Идентификатор товара в системе продавца — артикул   
* search {string} Поисĸ по содержанию записи, проверяет наличие.   
* sku {int64} Идентификатор товара в системе Ozon — SKU   
* visibility {enum} Фильтр по видимости товара   

<u>api</u>   

```
API.v1.report.products.prices.create.create(
    offer_id: StringType,
    search: StringType,
    sku: Int64Type,
    language: EnumType = DEFAULT,
    visibility: EnumType = ALL,
)
```   

# v1/report/returns/create

### POST

Отчёт содержит информацию о возвращённых товарах, которые приняты от покупателя, готовы к получению или переданы продавцу.

Метод подходит только для заказов, которые отправлены со склада продавца.

<u>body</u>   

* language {enum} Язык в ответе   
* filter {object} Фильтр   

<u>api</u>   

```
API.v1.report.returns.create.create(
    filter: ObjectType,
    language: EnumType = DEFAULT,
)
```   

# v1/report/stock/create

### POST

Отчёт с информацией о количестве доступных и зарезервированных единиц товара на складе.

<u>body</u>   

* language {enum} Язык в ответе   

<u>api</u>   

```
API.v1.report.stock.create.create(
    language: EnumType = DEFAULT,
)
```   

# v1/report/transactions/create

### POST

Отчёт по транзакциям с информацией о начислениях за выбранный период

* дата и тип начисления, * идентификатор отправления или услуги, * детали по отправлению или услуге, * сумма, полученная за продажу или удержанная за возврат, * комиссия за продажу, * сумма, удержанная за обработку и доставку, * сумма, удержанная за возврат и отмену, * общая сумма.

<u>body</u>   

* date_from {dateTimeTz} Дата, с которой рассчитывается отчёт по транзакциям.   
* date_to {dateTimeTz} Дата, по которую рассчитывается отчёт по транзакциям.   
* language {enum} Язык в ответе   
* search {string} Поиск по содержанию записи, проверяет наличие.   
* transaction_type {enum} Фильтр по типу транзакции   

<u>api</u>   

```
API.v1.report.transactions.create.create(
    date_from: DateTimeTzType,
    date_to: DateTimeTzType,
    search: StringType,
    language: EnumType = DEFAULT,
    transaction_type: EnumType = ALL,
)
```   

# v1/supplier/orders/:order_id/waybill_acceptance_results

### GET

Метод для получения списка накладных по номеру заявки.

<u>path</u>   

* order_id {int64} Номер заявки.   

<u>api</u>   

```
API.v1.supplier.orders.:order_id.waybill_acceptance_results.getByOrderId(
    order_id: Int64Type,
)
```   

# v1/supplier/waybill_acceptance_results/:waybill_id

### GET

Метод для получения результатов приёмки по номеру накладной.

<u>path</u>   

* waybill_id {int64} Номер накладной.   

<u>api</u>   

```
API.v1.supplier.waybill_acceptance_results.:waybill_id.getByWaybillId(
    waybill_id: Int64Type,
)
```   

# v1/warehouse/list

### POST

В запросе не нужно указывать параметры

Ваша компания будет определена по Client-ID.

<u>api</u>   

```
API.v1.warehouse.list.post()
```   

# v2/category/attribute/values

### POST

Справочник значений характеристики

<u>body</u>   

* attribute_id {int64} Идентификатор характеристики   
* category_id {int64} Идентификатор категории   
* language {enum} Язык в ответе   
* last_value_id {int64} Идентификатор справочника, с которого нужно начать ответ   
* limit {int64} Количество значений в ответе   

<u>api</u>   

```
API.v2.category.attribute.values.get(
    attribute_id: Int64Type,
    category_id: Int64Type,
    last_value_id: Int64Type,
    language: EnumType = DEFAULT,
    limit: Int64Type = 100,
)
```   

# v2/category/tree

### POST

Дерево категории товаров

Возвращает категории для товаров в виде дерева. Создание товаров доступно только в категориях последнего уровня, сравните именно эти категории с категориями своей площадки. Категории не создаются по запросу пользователя.

<u>body</u>   

* category_id {int64} Идентификатор категории   
* language {enum} Язык в ответе   

<u>api</u>   

```
API.v2.category.tree.get(
    category_id: Int64Type,
    language: EnumType = DEFAULT,
)
```   

# v2/fbs/posting/delivering

### POST

Перевести отправление в статус «Доставлено», если используется сторонняя служба доставки.

<u>body</u>   

* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v2.fbs.posting.delivering.set(
    posting_number: StringType,
)
```   

# v2/fbs/posting/delivering

### POST

Перевести отправление в статус «Доставляется», если используется сторонняя служба доставки.

<u>body</u>   

* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v2.fbs.posting.delivering.setStatus(
    posting_number: StringType,
)
```   

# v2/fbs/posting/last-mile

### POST

Перевести отправление в статус «Последняя миля», если используется сторонняя служба доставки.

<u>body</u>   

* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v2.fbs.posting.last-mile.set(
    posting_number: StringType,
)
```   

# v2/fbs/posting/send-by-seller

### POST

Перевести отправление в статус «Отправлено продавцом». Статус доступен только продавцам с первой милей, продающим из-за рубежа.

<u>body</u>   

* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v2.fbs.posting.send-by-seller.set(
    posting_number: StringType,
)
```   

# v2/fbs/posting/tracking-numbers/set

### POST

Добавить трек-номера к отправлениям.

<u>body</u>   

* tracking_numbers {array} Массив с парами идентификатор отправления — трек-номер.   

<u>api</u>   

```
API.v2.fbs.posting.tracking-numbers.set.set(
    tracking_numbers: TrackingNumberType|TrackingNumberType[],
)
```   

# v2/posting/fbo/get

### POST

Возвращает информацию об отправлении по его идентификатору.

<u>body</u>   

* posting_number {string} Номер отправления.   
* with {object} Дополнительные поля, которые нужно добавить в ответ.   

<u>api</u>   

```
API.v2.posting.fbo.get.post(
    posting_number: StringType,
    withArg: ObjectType,
)
```   

# v2/posting/fbo/list

### POST

Возвращает список отправлений за указанный период времени.

Дополнительно можно отфильтровать отправления по их статусу.

<u>body</u>   

* dir {enum} Направление сортировки   
* filter {object} Фильтр для поиска отправлений.   
* limit {int64} Количество значений в ответе   
* offset {int64} Количество элементов, которое будет пропущено в ответе.   
* translit {boolean} Если включена транслитерация адреса из кириллицы в латиницу — true.   
* with {object} Дополнительные поля, которые нужно добавить в ответ.   

<u>api</u>   

```
API.v2.posting.fbo.list.get(
    dir: EnumType,
    filter: ObjectType,
    offset: Int64Type,
    translit: BooleanType,
    withArg: ObjectType,
    limit: Int64Type = 100,
)
```   

# v2/posting/fbs/act/check-status

### POST

Получение текущего статуса формирования акта приёма-передачи и транспортной накладной.

<u>body</u>   

* id {int64} Номер задания на формирование документов (также идентификатор перевозки) из метода POST /v2/posting/fbs/act/create.   

<u>api</u>   

```
API.v2.posting.fbs.act.check-status.get(
    id: Int64Type,
)
```   

# v2/posting/fbs/act/get-container-labels

### POST

Метод создает этикетки для грузового места.

<u>body</u>   

* id {int64} Номер задания   

<u>api</u>   

```
API.v2.posting.fbs.act.get-container-labels.get(
    id: Int64Type,
)
```   

# v2/posting/fbs/act/get-pdf

### POST

Получить сформированные передаточные документы в формате PDF: акт приёма-передачи и транспортную накладную.

<u>body</u>   

* id {int64} Номер задания   

<u>api</u>   

```
API.v2.posting.fbs.act.get-pdf.get(
    id: Int64Type,
)
```   

# v2/posting/fbs/arbitration

### POST

Если отправление передано в доставку, но не просканировано в сортировочном центре, можно открыть спор.

Открытый спор переведёт отправление в статус arbitration.

<u>body</u>   

* posting_number {array}    

<u>api</u>   

```
API.v2.posting.fbs.arbitration.create(
    posting_number: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v2/posting/fbs/awaiting-delivery

### POST

Передает спорные заказы к отгрузке.

Статус отправления изменится на awaiting_deliver.

<u>body</u>   

* posting_number {array}    

<u>api</u>   

```
API.v2.posting.fbs.awaiting-delivery.create(
    posting_number: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v2/posting/fbs/cancel

### POST

Меняет статус отправления на cancelled.

Если вы используете схему rFBS, у вас доступны следующие идентификаторы причин отмены — cancel_reason_id: * 352 — товара нет в наличии; * 400 — остался только бракованный товар; * 401 — отмена из арбитража; * 402 — другая причина; * 665 — покупатель не забрал заказ; * 666 — отсутствует доставка в данный регион; * 667 — заказ утерян службой доставки. Для условно-доставленных заказов доступны только 3 последние причины. Если значение параметра cancel_reason_id — 402, заполните поле cancel_reason_message.

<u>body</u>   

* cancel_reason_id {enum} Идентификатор причины отмены отправления.   
* cancel_reason_message {string} Дополнительная информация по отмене.   
* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v2.posting.fbs.cancel.create(
    cancel_reason_id: EnumType,
    cancel_reason_message: StringType,
    posting_number: StringType,
)
```   

# v2/posting/fbs/cancel-reason/list

### POST

Возвращет список причин отмены отправлений.

<u>api</u>   

```
API.v2.posting.fbs.cancel-reason.list.get()
```   

# v2/posting/fbs/get-by-barcode

### POST

<u>body</u>   

* barcode {string} Штрихкод отправления.   

<u>api</u>   

```
API.v2.posting.fbs.get-by-barcode.get(
    barcode: StringType,
)
```   

# v2/posting/fbs/package-label

### POST

Генерирует PDF-файл с этикетками для указанных отправлений.

Если вы работаете по схеме rFBS, этикетки для отправлений печатать не нужно. В одном запросе можно передать не больше 20 идентификаторов. Если хотя бы для одного отправления возникнет ошибка, этикетки не будут подготовлены для всех отправлений в запросе. Рекомендуем запрашивать этикетки через 45–60 секунд после сборки заказа. Ошибка The next postings aren't ready означает, что этикетки ещё не готовы, повторите запрос позднее.

<u>body</u>   

* posting_number {array}    

<u>api</u>   

```
API.v2.posting.fbs.package-label.get(
    posting_number: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v2/posting/fbs/product/cancel

### POST

Используйте метод, если вы не можете отправить часть продуктов из отправления.

Идентификаторы причин отмены cancel_reason_id при работе по схеме rFBS: * 352 — товара нет в наличии; * 400 — остался только бракованный товар; * 401 — отмена из арбитража; * 402 — другая причина; * 665 — покупатель не забрал заказ; * 666 — нет доставки в этот регион; * 667 — заказ утерян службой доставки. Для условно-доставленных заказов доступны только 3 последние причины. Если значение параметра cancel_reason_id — 402, заполните поле cancel_reason_message.

<u>body</u>   

* cancel_reason_id {enum} Идентификатор причины отмены отправления.   
* cancel_reason_message {string} Дополнительная информация по отмене.   
* items {array} Информация о товарах.   
* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v2.posting.fbs.product.cancel.create(
    cancel_reason_id: EnumType,
    cancel_reason_message: StringType,
    items: DefaultItemNameType|DefaultItemNameType[],
    posting_number: StringType,
)
```   

# v2/posting/fbs/product/change

### POST

<u>body</u>   

* items {array} Информация о товарах.   
* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v2.posting.fbs.product.change.change(
    items: ItemType|ItemType[],
    posting_number: StringType,
)
```   

# v2/posting/fbs/product/country/list

### POST

Метод для получения списка доступных стран-изготовителей и их ISO кодов.

<u>body</u>   

* name_search {string} Фильтрация по строке.   

<u>api</u>   

```
API.v2.posting.fbs.product.country.list.get(
    name_search: StringType,
)
```   

# v2/posting/fbs/product/country/set

### POST

Метод для добавления на продукт атрибута «Страна-изготовитель», если он не был указан.

<u>body</u>   

* posting_number {string} Номер отправления.   
* product_id {int64} Идентификатор товара   
* country_iso_code {string} Двухбуквенный код добавляемой страны по стандарту ISO_3166-1.   

<u>api</u>   

```
API.v2.posting.fbs.product.country.set.add(
    posting_number: StringType,
    product_id: Int64Type,
    country_iso_code: StringType,
)
```   

# v2/posting/fbs/ship

### POST

Делит заказ на отправления и переводит его в статус awaiting_deliver.

Каждый элемент items описывает отдельное отправление в заказе. Разделить заказ нужно, если: * товары не помещаются в одну упаковку, * товары нельзя сложить в одну упаковку.

<u>body</u>   

* packages {array} Список посылок.   
* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v2.posting.fbs.ship.create(
    packages: DefaultItemNameType|DefaultItemNameType[],
    posting_number: StringType,
)
```   

# v2/product/import

### POST

Метод позволяет создавать товары и обновлять информацию о товарах.

В сутки можно создать или обновить определённое количество товаров. Чтобы узнать лимит, используйте /v2/product/info/limit. Если количество загрузок и обновлений товаров превысит лимит, появится ошибка item_limit_exceeded. В одном запросе можно передать до 100 товаров. Каждый товар — это отдельный элемент в массиве items. Укажите всю информацию о товаре: его характеристики, штрихкод, изображения, габариты и цену. Характеристики зависят от категории товара. Вы можете посмотреть список обязательных характеристик для некоторых категорий в Помощи или методом /v3/category/attribute. Для некоторых характеристик можно использовать HTML-теги.

<u>body</u>   

* items {array}    

<u>api</u>   

```
API.v2.product.import.createOrUpdate(
    items: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v2/product/info

### POST

<u>body</u>   

* offer_id {string} Идентификатор товара в системе продавца — артикул   
* product_id {int64} Идентификатор товара   
* sku {int64} Идентификатор товара в системе Ozon — SKU   

<u>api</u>   

```
API.v2.product.info.get(
    offer_id: StringType,
    product_id: Int64Type,
    sku: Int64Type,
)
```   

# v2/product/info/limit

### POST

<u>api</u>   

```
API.v2.product.info.limit.get()
```   

# v2/product/info/list

### POST

Метод для получения массива товаров по их идентификаторам

В теле запроса должен быть массив однотипных идентификаторов, в ответе будет массив items. Внутри items для каждого товара поля совпадают с /v2/product/info.

<u>body</u>   

* offer_id {array}    
* product_id {array}    
* sku {array}    

<u>api</u>   

```
API.v2.product.info.list.get(
    offer_id: DefaultItemNameType|DefaultItemNameType[],
    product_id: DefaultItemNameType|DefaultItemNameType[],
    sku: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v2/product/list

### POST

<u>body</u>   

* filter {object} Фильтр по товарам   
* last_id {string} Идентификатор последнего значения на странице   
* limit {int64} Количество значений в ответе   

<u>api</u>   

```
API.v2.product.list.get(
    filter: ObjectType,
    last_id: StringType,
    limit: Int64Type = 100,
)
```   

# v2/products/delete

### POST

В одном запросе можно передать до 500 идентификаторов

<u>body</u>   

* products {array} Идентификатор товара   

<u>api</u>   

```
API.v2.products.delete.post(
    products: DefaultItemNameType|DefaultItemNameType[],
)
```   

# v2/products/stocks

### POST

Позволяет изменить информацию о количестве товара в наличии

За один запрос можно изменить наличие для 100 товаров. В минуту можно отправить до 80 запросов. Задать наличие товара возможно только после того, как его статус сменится на processed. Остатки крупногабаритных товаров можно обновлять только на предназначенных для них складах.

<u>body</u>   

* offer_id {string} Идентификатор товара в системе продавца — артикул   
* product_id {int64} Идентификатор товара   
* stock {int64} Количество   
* warehouse_id {int64} Идентификатор склада, полученный из метода /v1/warehouse/list   

<u>api</u>   

```
API.v2.products.stocks.update(
    offer_id: StringType,
    product_id: Int64Type,
    stock: Int64Type,
    warehouse_id: Int64Type,
)
```   

# v2/returns/company/fbo

### POST

Позволяет получить информацию о возвращённых товарах, которые продаются со склада Ozon.

<u>body</u>   

* filter {object} Фильтр.   
* limit {int64} Количество значений в ответе   
* offset {int64} Количество элементов, которое будет пропущено в ответе.   

<u>api</u>   

```
API.v2.returns.company.fbo.get(
    filter: ObjectType,
    offset: Int64Type,
    limit: Int64Type = 100,
)
```   

# v2/returns/company/fbs

### POST

Позволяет получить информацию о возвращённых товарах, которые продаются со склада продавца.

<u>body</u>   

* filter {object}    
* limit {int64} Количество значений в ответе   
* offset {int64} Количество элементов, которое будет пропущено в ответе.   

<u>api</u>   

```
API.v2.returns.company.fbs.get(
    filter: ObjectType,
    offset: Int64Type,
    limit: Int64Type = 100,
)
```   

# v3/category/attribute

### POST

Список характеристик категории

Получение характеристик для указанной категории товаров. Передавайте не более 20 идентификаторов категорий в списке category_id.

<u>body</u>   

* category_id {array}    
* language {enum} Язык в ответе   
* attribute_type {enum} Фильтр по характеристикам   

<u>api</u>   

```
API.v3.category.attribute.get(
    category_id: DefaultItemNameType|DefaultItemNameType[],
    language: EnumType = DEFAULT,
    attribute_type: EnumType = ALL,
)
```   

# v3/finance/transaction/list

### POST

Возвращает подробную информацию по всем начислениям.

Максимальный период, за который можно получить информацию в одном запросе — 3 месяца. Если в запросе не указывать posting_number, то в ответе будут все отправления за указанный период или отправления определённого типа.

<u>body</u>   

* filter {object} Фильтр.   
* page {int64} Номер страницы, возвращаемой в запросе.   
* page_size {int64} Количество элементов на странице.   

<u>api</u>   

```
API.v3.finance.transaction.list.get(
    filter: ObjectType,
    page: Int64Type,
    page_size: Int64Type,
)
```   

# v3/finance/transaction/totals

### POST

Возвращает итоговые суммы по транзакциям за указанный период.

<u>body</u>   

* date {object} Фильтр по дате.   
* posting_number {string} Номер отправления.   
* transaction_type {enum}    

<u>api</u>   

```
API.v3.finance.transaction.totals.get(
    date: ObjectType,
    posting_number: StringType,
    transaction_type: EnumType,
)
```   

# v3/posting/fbs/get

### POST

<u>body</u>   

* posting_number {string} Номер отправления.   
* with {object} Дополнительные поля, которые нужно добавить в ответ.   

<u>api</u>   

```
API.v3.posting.fbs.get.get(
    posting_number: StringType,
    withArg: ObjectType,
)
```   

# v3/posting/fbs/list

### POST

Возвращает список отправлений за указанный период времени.

Дополнительно можно отфильтровать отправления по их статусу. has_next = true в ответе может значить, что вернули не весь массив отправлений. Чтобы получить информацию об остальных отправлениях, сделайте новый запрос с другим значением offset.

<u>api</u>   

```
API.v3.posting.fbs.list.get()
```   

# v3/posting/fbs/set

### POST

Делит заказ на отправления и переводит его в статус awaiting_deliver.

Каждый элемент items описывает отдельное отправление в заказе. Разделить заказ нужно, если: * товары не помещаются в одну упаковку, * товары нельзя сложить в одну упаковку. Отличается от /v2/posting/fbs/ship наличием в запросе параметра exemplar_info. При необходимости укажите номер грузовой таможенной декларации в параметре gtd. Если его нет, передайте значение is_gtd_absent = true.

<u>body</u>   

* packages {array} Список пакетов, на которые делится отправление.   
* posting_number {string} Номер отправления.   
* with {object} Параметр для выдачи дополнительных полей в ответе.   

<u>api</u>   

```
API.v3.posting.fbs.set.create(
    packages: DefaultItemNameType|DefaultItemNameType[],
    posting_number: StringType,
    withArg: ObjectType,
)
```   

# v3/posting/fbs/ship/package

### POST

Если в запросе передать часть продуктов из отправления, то в результате обработки запроса первичное отправление разделится на две части.

В первичном несобранном отправлении останется часть продуктов, которую не передали в запросе. Статус изначального отправления изменится только после изменения статуса отправлений, на которые он разделился.

<u>body</u>   

* posting_number {string} Номер отправления.   
* products {array} Список продуктов в пакете.   

<u>api</u>   

```
API.v3.posting.fbs.ship.package.create(
    posting_number: StringType,
    products: ProductType|ProductType[],
)
```   

# v3/posting/fbs/unfulfilled/list

### POST

Возвращает список необработанных отправлений cо статусами: * awaiting_packaging — готов к сборке, * not_accepted — не принято, * awaiting_deliver — готов к отгрузке.

<u>api</u>   

```
API.v3.posting.fbs.unfulfilled.list.get()
```   

# v3/product/info/stocks

### POST

Возвращает информацию о ĸоличестве товаров на сĸладах

Сĸольĸо единиц есть в наличии, сĸольĸо зарезервировано поĸупателями.

<u>body</u>   

* filter {object} Фильтр по товарам   
* last_id {string} Идентификатор последнего значения на странице   
* limit {int64} Количество значений в ответе   

<u>api</u>   

```
API.v3.product.info.stocks.get(
    filter: ObjectType,
    last_id: StringType,
    limit: Int64Type = 100,
)
```   

# v3/products/info/attributes

### POST

Возвращает описание характеристик товара по его идентификатору

Товар можно искать по offer_id или product_id.

<u>body</u>   

* filter {object} Фильтр по товарам   
* last_id {string} Идентификатор последнего значения на странице   
* limit {int64} Количество значений в ответе   
* sort_by {string} Параметр, по которому товары будут отсортированы   
* sort_dir {string} Направление сортировки   

<u>api</u>   

```
API.v3.products.info.attributes.get(
    filter: ObjectType,
    last_id: StringType,
    sort_by: StringType,
    sort_dir: StringType,
    limit: Int64Type = 100,
)
```   

# v3/products/info/stocks

### POST

Возвращает информацию о ĸоличестве товаров на сĸладах

Сĸольĸо единиц есть в наличии, сĸольĸо зарезервировано поĸупателями.

<u>body</u>   

* filter {object} Фильтр по товарам   
* last_id {string} Идентификатор последнего значения на странице   
* limit {int64} Количество значений в ответе   

<u>api</u>   

```
API.v3.products.info.stocks.get(
    filter: ObjectType,
    last_id: StringType,
    limit: Int64Type = 100,
)
```   

# v4/fbs/posting/product/exemplar/set

### POST

Асинхронный метод: * для проверки наличия экземпляров в обороте в системе «Честный ЗНАК»; * для сохранения данных экземпляров.

Чтобы получить результаты проверок, используйте метод /v4/fbs/posting/product/exemplar/status. При необходимости укажите номер грузовой таможенной декларации в параметре gtd. Если его нет, передайте значение is_gtd_absent = true. Если у вас несколько одинаковых товаров в отправлении, укажите один product_id и массив exemplars для каждого товара из отправления. Всегда передавайте полный набор данных по экземплярам и продуктам. Например, в вашей системе 10 экземпляров. Вы передали их для проверки и сохранения. Потом добавили в своей системе ещё 60 экземпляров. При повторной передаче экземпляров для проверки и сохранения укажите все экземпляры: и старые, и только что добавленные.

<u>body</u>   

* posting_number {string} Номер отправления.   
* products {array}    

<u>api</u>   

```
API.v4.fbs.posting.product.exemplar.set.checkAndSave(
    posting_number: StringType,
    products: ProductType|ProductType[],
)
```   

# v4/fbs/posting/product/exemplar/status

### POST

Метод для получения статусов проверки экземпляров, переданных в методе /v4/fbs/posting/product/exemplar/set. 

Также возвращает данные по этим экземплярам.

<u>body</u>   

* posting_number {string} Номер отправления.   

<u>api</u>   

```
API.v4.fbs.posting.product.exemplar.status.get(
    posting_number: StringType,
)
```   

# v4/fbs/posting/product/exemplar/validate

### POST

Метод для проверки кодов на соответствие требованиям системы «Честный ЗНАК» по количеству и составу символов.

Если у вас нет номера грузовой таможенной декларации (ГТД), вы можете его не указывать.

<u>body</u>   

* posting_number {string} Номер отправления.   
* products {array} Список товаров.   

<u>api</u>   

```
API.v4.fbs.posting.product.exemplar.validate.check(
    posting_number: StringType,
    products: ProductType|ProductType[],
)
```   

# v4/posting/fbs/ship

### POST

Делит заказ на отправления и переводит его в статус awaiting_deliver.

Каждый элемент items описывает отдельное отправление в заказе. Разделить заказ нужно, если: * товары не помещаются в одну упаковку, * товары нельзя сложить в одну упаковку. Отличается от /v3/posting/fbs/ship отсутствием передачи информации по экземплярам в запросе.

<u>body</u>   

* packages {array} Список пакетов, на которые делится отправление.   
* posting_number {string} Номер отправления.   
* with {object} Дополнительная информация.   

<u>api</u>   

```
API.v4.posting.fbs.ship.create(
    packages: PackageType|PackageType[],
    posting_number: StringType,
    withArg: ObjectType,
)
```   

# v4/product/info/prices

### POST

В запросе вы можете передать максимум 1000 товаров

<u>body</u>   

* filter {object} Фильтр по товарам   
* last_id {string} Идентификатор последнего значения на странице   
* limit {int64} Количество значений в ответе   

<u>api</u>   

```
API.v4.product.info.prices.get(
    filter: ObjectType,
    last_id: StringType,
    limit: Int64Type = 100,
)
```   
