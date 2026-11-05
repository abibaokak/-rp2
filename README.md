# FourMaces + WellyGUI — ресурспаки

Красивый ресурспак для **Божественной булавы** из плагина FourMaces
и **золотое оформление всех GUI** для плагина WellyGUI.

Булава получает кастомную модель через `CustomModelData: 421001`.

В плагине FourMaces 1.1.0 (config-version 5) Божественная булава по умолчанию
получает **Density X**, **Breach X** и **Fire Aspect V**, а сам плагин умеет
отправлять пак игрокам (секция `resource-pack` в `config.yml`).

WellyGUI 1.0.0 отправляет отдельный пак `wellygui-style.zip`: он перекрашивает
текстуры контейнеров в лимонно-золотую гамму с орнаментами (дамаск, крупные
цветы-розетки на блок клеток, фирменные плашки) и меняет заголовки GUI в `ru_ru`/`en_us`,
включая инвентарь по клавише **E** (его нельзя переименовать через Bukkit/Paper).

## Файлы

| Файл | Что внутри | Ссылка |
|---|---|---|
| `pugalopack.zip` | Candy Halloween **+** FourMaces God Mace | `https://raw.githubusercontent.com/abibaokak/-rp2/main/pugalopack.zip` |
| `fourmaces-godmace.zip` | Только FourMaces God Mace | `https://raw.githubusercontent.com/abibaokak/-rp2/main/fourmaces-godmace.zip` |
| `wellygui-style.zip` | Золотые GUI для WellyGUI (контейнеры + E) | `https://raw.githubusercontent.com/abibaokak/-rp2/main/wellygui-style.zip` |

`pugalopack.zip` специально лежит по старому адресу Candy-плагина:
`https://raw.githubusercontent.com/abibaokak/-rp2/main/pugalopack.zip`.
Поэтому Candy продолжит работать, а Божественная булава получит новую текстуру
без дополнительной настройки.

## Установка

### Вариант 1 — плагин FourMaces сам отправляет пак (проще всего)

В `plugins/FourMaces/config.yml`:

```yaml
resource-pack:
  enabled: true
  url: 'https://raw.githubusercontent.com/abibaokak/-rp2/main/fourmaces-godmace.zip'
  cache-bust: true
```

После `/fourmaces reload` или перезахода пак приходит автоматически.
Проверить: `/fourmaces diag` (должен показать `CustomModelData: 421001`)
и `/fourmaces pack all`, чтобы отправить пак повторно.

Если ссылка на GitHub недоступна, загрузите `plugins/FourMaces/fourmaces-godmace.zip`
на свой хостинг и укажите его адрес в `url`.

### Вариант 2 — WellyGUI отправляет золотое оформление GUI

В `plugins/WellyGUI/config.yml`:

```yaml
resource-pack:
  enabled: true
  url: 'https://raw.githubusercontent.com/abibaokak/-rp2/main/wellygui-style.zip'
  cache-bust: true
```

После `/wellygui reload` или перезахода пак приходит автоматически.
Повторно отправить всем: `/wellygui pack`.

### Вариант 3 — через Candy

В `plugins/Candy/config.yml` уже должен быть адрес:

```yaml
resource-pack:
  send: true
  url: 'https://raw.githubusercontent.com/abibaokak/-rp2/main/pugalopack.zip'
```

Перезапустите сервер. Candy отправит объединённый пак: конфеты и Божественная булава.
Если Candy раздаёт пак, в FourMaces поставьте `resource-pack.enabled: false`,
чтобы клиенту не предлагали два пака.

### Вариант 4 — стандартный resource pack

Пропишите в `server.properties`:

```properties
resource-pack=https://raw.githubusercontent.com/abibaokak/-rp2/main/fourmaces-godmace.zip
resource-pack-sha1=a683c1e97fdd6ea08cff526b16fd4594de420a02
resource-pack-prompt={"text":"Установите ресурспак FourMaces","color":"gold"}
```

Или укажите этот адрес в вашем плагине resource-pack.

## SHA1

| Файл | SHA1 |
|---|---|
| `fourmaces-godmace.zip` | `a683c1e97fdd6ea08cff526b16fd4594de420a02` |
| `pugalopack.zip` | `466badc38efda038fe6328cb62e53641992dcf06` |
| `wellygui-style.zip` | `4edbaa9b948db6e81687ba0c5dce6f7bdb014ba1` |

## Совместимость

* **Minecraft 1.21.1–1.21.3** — используется legacy-модель с `overrides` и `custom_model_data`.
* **Minecraft 1.21.4–1.21.11+** — используется современный формат `assets/minecraft/items/mace.json`.
* Диапазон форматов пака: `34–99` (`supported_formats`, `min_format`/`max_format`),
  поэтому пак принимается и старыми клиентами (в том числе через ViaVersion),
  и актуальными версиями.
* Пак не требует Oraxen или ItemsAdder. Достаточно ванильной булавы с `CustomModelData: 421001`.
* В объединённом паке для старых клиентов добавлены и legacy-overrides для конфеты Candy.

## Как получить Божественную булаву

1. Скрафтите 4 обычные булавы FourMaces.
2. Положите их в верстак 3×3 углами или крестом.
3. В центр положите Звезду Незера.
4. После крафта Божественная булава автоматически получит модель из этого пака,
   Density X, Breach X и Fire Aspect V.

Если Божественную булаву уничтожить (пустота, взрыв, поломка, очистка плагином), рецепт снова
откроется — при включённой настройке `reset-god-craft-on-destruction: true`.
Булава по умолчанию огнестойкая, поэтому лава её не уничтожает.

## Если модель не появилась

1. Выполните `/fourmaces diag` — команда покажет `CustomModelData` предмета в руке
   и статус пака у клиента. Если CMD нет, выполните `/fourmaces refresh`.
2. Убедитесь, что пак вообще отправляется: в консоли при входе должна быть строка
   `Ресурспак отправлен игроку ...`. Если её нет — включите `resource-pack.enabled: true`
   (или настройте Candy).
3. Если у игрока `FAILED_DOWNLOAD` — ссылка недоступна с его стороны (GitHub может
   блокироваться провайдером). Загрузите `fourmaces-godmace.zip` на свой хостинг
   и поменяйте `resource-pack.url`.
4. Булавы, созданные до обновления, не имеют `CustomModelData`. Выполните
   `/fm refresh` — плагин обновит предметы в инвентарях, эндер-сундуках, на земле,
   в рамках и в загруженных контейнерах. Также это происходит автоматически при входе игрока.
5. Чистая папка `.minecraft/server-resource-packs` означает, что клиент ещё ни разу
   не скачивал серверный пак. После успешной загрузки в ней появится файл.
6. Если установлен Oraxen или ItemsAdder и у него есть предмет `god_mace`,
   внешний вид берётся из него. Отключите `use-oraxen` / `use-itemsadder` в конфиге
   FourMaces, чтобы использовать модель из этого пака.
