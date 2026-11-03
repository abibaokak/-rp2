# FourMaces — God Mace Resource Pack

Красивый ресурспак для **Божественной булавы** из плагина FourMaces.
Булава получает кастомную модель через `CustomModelData: 421001`.

В плагине FourMaces 1.0.0 (config-version 2) Божественная булава по умолчанию
получает **Density VII** и **Breach VII**.

## Файлы

| Файл | Что внутри | Ссылка |
|---|---|---|
| `pugalopack.zip` | Candy Halloween **+** FourMaces God Mace | `https://raw.githubusercontent.com/abibaokak/-rp2/main/pugalopack.zip` |
| `fourmaces-godmace.zip` | Только FourMaces God Mace | `https://raw.githubusercontent.com/abibaokak/-rp2/main/fourmaces-godmace.zip` |

`pugalopack.zip` специально лежит по старому адресу Candy-плагина:
`https://raw.githubusercontent.com/abibaokak/-rp2/main/pugalopack.zip`.
Поэтому Candy продолжит работать, а Божественная булава получит новую текстуру
без дополнительной настройки.

## Установка

### Вариант 1 — через Candy (рекомендуется)

В `plugins/Candy/config.yml` уже должен быть адрес:

```yaml
resource-pack:
  send: true
  url: 'https://raw.githubusercontent.com/abibaokak/-rp2/main/pugalopack.zip'
```

Перезапустите сервер. Candy отправит объединённый пак: конфеты и Божественная булава.

### Вариант 2 — стандартный resource pack

Пропишите в `server.properties`:

```properties
resource-pack=https://raw.githubusercontent.com/abibaokak/-rp2/main/fourmaces-godmace.zip
resource-pack-sha1=7e246910e43f8a69d88a9d210e7313d8caca3f84
resource-pack-prompt={"text":"Установите ресурспак FourMaces","color":"gold"}
```

Или укажите этот адрес в вашем плагине resource-pack.

## SHA1

| Файл | SHA1 |
|---|---|
| `fourmaces-godmace.zip` | `7e246910e43f8a69d88a9d210e7313d8caca3f84` |
| `pugalopack.zip` | `45fbf63cb39e2c58441645bdd99524293c1e0fec` |

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
   Density VII и Breach VII.

Если Божественную булаву уничтожить (пустота, взрыв, поломка, очистка плагином), рецепт снова
откроется — при включённой настройке `reset-god-craft-on-destruction: true`.
Булава по умолчанию огнестойкая, поэтому лава её не уничтожает.

## Если модель не появилась

1. Убедитесь, что сервер отправляет именно `pugalopack.zip` (или `fourmaces-godmace.zip`).
2. Перезайдите на сервер: Candy отправляет пак при входе.
3. Булавы, созданные до обновления, не имеют `CustomModelData`. Выполните
   `/fm refresh` — плагин обновит предметы в инвентарях, эндер-сундуках, на земле,
   в рамках и в загруженных контейнерах. Также это происходит автоматически при входе игрока.
4. Если клиент закешировал старую версию пака, очистите папку
   `.minecraft/server-resource-packs` и подключитесь заново.
5. Если установлен Oraxen или ItemsAdder и у него есть предмет `god_mace`,
   внешний вид берётся из него. Отключите `use-oraxen` / `use-itemsadder` в конфиге
   FourMaces, чтобы использовать модель из этого пака.
