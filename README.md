# FourMaces — God Mace Resource Pack

Красивый ресурспак для **Божественной булавы** из плагина FourMaces.
Булава получает кастомную модель через `CustomModelData: 421001`.

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
resource-pack-sha1=4aad9a9160a59fbd4b7926ee6021403479a2f565
resource-pack-prompt={"text":"Установите ресурспак FourMaces","color":"gold"}
```

Или укажите этот адрес в вашем плагине resource-pack.

## SHA1

| Файл | SHA1 |
|---|---|
| `fourmaces-godmace.zip` | `4aad9a9160a59fbd4b7926ee6021403479a2f565` |
| `pugalopack.zip` | `0dc9131a798d941bde3be83c6cbfef4854e2d6b7` |

## Совместимость

* **Minecraft 1.21.4+** — используется современный формат `assets/minecraft/items/mace.json`.
* **Minecraft 1.21.1–1.21.3** — используется legacy-модель с `overrides` и `custom_model_data`.
* Пак не требует Oraxen или ItemsAdder. Достаточно ванильной булавы с `CustomModelData: 421001`.

## Как получить Божественную булаву

1. Скрафтите 4 обычные булавы FourMaces.
2. Положите их в верстак 3×3 углами или крестом.
3. В центр положите Звезду Незера.
4. После крафта Божественная булава автоматически получит модель из этого пака.

Если Божественную булаву уничтожить (пустота, взрыв, поломка, очистка плагином), рецепт снова
откроется — при включённой настройке `reset-god-craft-on-destruction: true`.
Булава по умолчанию огнестойкая, поэтому лава её не уничтожает.
