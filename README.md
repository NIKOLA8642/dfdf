# Распределённый вычислитель арифметических выражений
Эта система предназначена для обработки арифметических выражений в распределённом режиме. Она вычисляет каждый пример отдельно и вместо немедленного ответа возвращает уникальный идентификатор (ID), по которому можно получить результат после его обработки.

# Как им пользоваться
Шаг 1: Установка Docker
Если Docker не установлен, скачайте и установите его с официального сайта: https://www.docker.com/products/docker-desktop/.

Шаг 2: Запуск проекта
Запустите Docker.

В терминале перейдите в директорию проекта и выполните команду:

bash
docker-compose up --build
Шаг 3: Отправка запроса
В PowerShell отправьте POST-запрос с выражением, которое вы хотите вычислить. Например:

powershell
Invoke-RestMethod -Uri "http://localhost:8080/api/v1/calculate" -Method Post -Headers @{"Content-Type"="application/json"} -Body '{"expression": "2 + 2 * 2"}'
Шаг 4: Получение идентификатора
В ответе на запрос вы получите уникальный ID для вашего выражения.

Шаг 5: Получение результата
Используйте полученный ID, чтобы получить результат вычисления. Для этого выполните команду:

powershell
$id = "9f1e38bb-2670-4526-9bdc-5b39b744c6fb"
$url = "http://localhost:8080/api/v1/expressions/$id"
$response = Invoke-RestMethod -Uri $url -Method Get
$response
Вместо "9f1e38bb-2670-4526-9bdc-5b39b744c6fb" вставьте ваш ID.

Пример ответа
В ответе вы получите объект, содержащий ID выражения, само выражение, статус обработки и результат вычисления:

json
{
  "id": "9f1e38bb-2670-4526-9bdc-5b39b744c6fb",
  "expression": "2 + 2 * 2",
  "status": "ЗАВЕРШЕНО",
  "result": 6
}
Остановка калькулятора
Если нужно остановить калькулятор, проверьте терминал и нажмите Ctrl + C.
