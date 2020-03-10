<!-- English version translation -->

# .osu (формат файла)

**.osu** — читабельный файловый формат, содержащий информацию о карте.

## Структура

Первая строка файла содержит версию карты, например, `osu file format v14` - новейшая версия

Последующие строки разделены в несколько разделов, обозначенных квадратными скобками:

| Раздел | Описание | Тип содержимого |
| :-- | :-- | :-- |
| `[General]` | Основная информация о карте | Набор пар `Ключ: значение` |
| `[Editor]` | Содержит настройки редактора карт | Набор пар `Ключ: значение` |
| `[Metadata]` | Информация для идентификации карты | Набор пар `Ключ: значение` |
| `[Difficulty]` | Настройки сложности | Набор пар `Ключ: значение` |
| `[Events]` | События карты и сториборда | Списки, разделенные запятыми |
| `[TimingPoints]` | Ключевые точки времени | Списки, разделенные запятыми |
| `[Colours]` | Цвета комбо и скина | Набор пар `Ключ: значение` |
| `[HitObjects]` | Игровые элементы карты (ноты, слайдеры, спиннеры) | Списки, разделенные запятыми |

## Разделы

### General

| Ключ | Тип переменной | Описание | Стандартное значение |
| :-- | :-- | :-- | :-- |
| `AudioFilename` | Строка | Расположение аудиофайла относительно текущего каталога |  |
| `AudioLeadIn` | Число | Время (в мс.) тишины перед началом вопсроизведения аудио | 0 |
| `AudioHash` | Строка | *Устарело* |  |
| `PreviewTime` | Число | Момент, с которого аудио должно проигрываться в меню выбора песни | -1 |
| `Countdown` | Число | Скорость обратного отсчета перед первым объектом (`0` = без обратного отсчета, `1` = обычный, `2` = замедленный, `3` = ускоренный) | 1 |
| `SampleSet` | Строка | Используемый набор семплов, если не перезаписано ключевыми точками времени (`Normal`, `Soft`, `Drum`) | Normal |
| `StackLeniency` | Число с запятой | Множитель частоты стакинга близкорасположенных объектов (0–1) | 0.7 |
| `Mode` | Чисто | Игровой режим (`0` = osu!, `1` = osu!taiko, `2` = osu!catch, `3` = osu!mania) | 0 |
| `LetterboxInBreaks` | Логический | Указывает, будет ли применяться леттербоксинг во время перерывов | 0 |
| `StoryFireInFront` | Логический | *Устарело* | 1 |
| `UseSkinSprites` | Логический | Указывает, использует ли сториборд элементы пользовательского скина images | 0 |
| `AlwaysShowPlayfield` | Логический | *Устарело* | 0 |
| `OverlayPosition` | Строка | Порядок отрисовки оверлея ноты относительно числа ноты (`NoChange` = использовать настроки скина, `Below` = рисовать оверлей под цифрами, `Above` = рисовать оверлей над цифрами) | NoChange |
| `SkinPreference` | Строка | Предпочитаемый скин для сипользвоания во время игры |  |
| `EpilepsyWarning` | Логический | Указывает необходимость уведомления о мерцающих цветах в начале карты | 0 |
| `CountdownOffset` | Число | Число с которого начинает обрытный отсчет перед первым объектом | 0 |
| `SpecialStyle` | Логический | Указывает использвоание раскладки "N+1" для osu!mania | 0 |
| `WidescreenStoryboard` | Логический | Указывает, поддерживает ли сториборд широкие экран | 0 |
| `SamplesMatchPlaybackRate` | Логический | Указывает необходимость изменения скорости звуковых семплов при использовании временных модов | 0 |

### Editor

Эти настройки используются только при открытии карты в [редакторе карт](/wiki/Beatmap_Editor). Они не влияют на гемплей.

| Ключ | Тип переменной | Описание |
| :-- | :-- | :-- |
| `Bookmarks` | Список чисел, разделенных запятыми | Время закладки, в миллисекундах |
| `DistanceSpacing` | Число с запятой | Множитель расстояния между соседними объектами (спейсинга) |
| `BeatDivisor` | Число с запятой | Шаг временной шкалы |
| `GridSize` | Число | Размер сетки элементов |
| `TimelineZoom` | Число с запятой | Масштаб временной шкалы |

### Metadata

| Ключ | Тип переменной | Описание |
| :-- | :-- | :-- |
| `Title` | Строка | Романизированное название песни (только Латиница) |
| `TitleUnicode` | Строка | Название песни (символы Юникода) |
| `Artist` | Строка | Романизированное имя исполнителя/группы(только Латиница) |
| `ArtistUnicode` | Строка | Имя исполнителя/группы (символы Юникода) |
| `Creator` | Строка | Создатель карты |
| `Version` | Строка | Название сложности карты (`[someone's insane]`) |
| `Source` | Строка | Оригинальное произведение, для которого песня была создана |
| `Tags` | Строки, разделённые пробелами | Поисковые ключевые слова |
| `BeatmapID` | Integer | ID карты |
| `BeatmapSetID` | Integer | ID сета карт |

### Difficulty

| Ключ | Тип переменной | Описание |
| :-- | :-- | :-- |
| `HPDrainRate` | Число с запятой | Скорость уменьшения полоски жизни (0–10) |
| `CircleSize` | Число с запятой | Размер нот (Circle Size) (0–10) |
| `OverallDifficulty` | Число с запятой | Точность нажатия (0–10) |
| `ApproachRate` | Число с запятой | Скорость появления объектов на экране (0–10) |
| `SliderMultiplier` | Число с запятой | Базовая скорость слайдеров, измеряемая в виртуальных [osu!pixels](/wiki/Glossary#osupixel) на один бит <!-- TODO: this prefix sounds awful ಠ_ಠ --> |
| `SliderTickRate` | Число с запятой | Количество слайдертиков на один бит |

### Events

*Синтаксис события:* `типСобытия,начальноеВремя,параметрыСобытия`

- **`eventType` (String or Integer):** Type of the event. Some events may be referred to by either a name or a number.
- **`startTime` (Integer):** Start time of the event, in milliseconds from the beginning of the beatmap's audio. For events that do not use a start time, the default is `0`.
- **`eventParams` (Comma-separated list):** Extra parameters specific to the event's type.

### Backgrounds

*Background syntax:* `0,0,filename,xOffset,yOffset`

- **`filename` (String):** Location of the background image relative to the beatmap directory. Double quotes are usually included surrounding the filename, but they are not required.
- **`xOffset` (Integer)** and **`yOffset` (Integer):** Offset in [osu! pixels](/wiki/Glossary#osupixel) from the center of the screen. For example, an offset of `50,100` would have the background shown 50 osu! pixels to the right and 100 osu! pixels down from the center of the screen. If the offset is `0,0`, writing it is optional.

### Videos

*Video syntax:* `Video,startTime,filename,xOffset,yOffset`

`Video` may be replaced by `1`.

- **`filename` (String)**, **`xOffset` (Integer)**, and **`yOffset` (Integer)** behave exactly as in backgrounds.

### Breaks

*Break syntax:* `2,startTime,endTime`

`2` may be replaced by `Break`.

- **`endTime` (Integer):** End time of the break, in milliseconds from the beginning of the beatmap's audio.

### Storyboards

*For information about storyboard syntax, see [Storyboard Scripting](/wiki/Storyboard_Scripting).*

Storyboards can be defined in a separate optional storyboard file with the `.osb` extension. External storyboards are shared between all beatmaps in a beatmapset.

Each beatmap may contain its own difficulty-specific storyboard, either in conjunction with the external storyboard or by itself.

## Timing points

Each timing point influences a specified portion of the map, commonly called a "timing section". The `.osu` file format requires these to be sorted in chronological order.

*Timing point syntax:* `time,beatLength,meter,sampleSet,sampleIndex,volume,uninherited,effects`

- **`time` (Integer):** Start time of the timing section, in milliseconds from the beginning of the beatmap's audio. The end of the timing section is the next timing point's time (or never, if this is the last timing point).
- **`beatLength` (Decimal):** This property has two meanings:
  - For uninherited timing points, the duration of a beat, in milliseconds.
  - For inherited timing points, a negative inverse slider velocity multiplier, as a percentage. For example, `-50` would make all sliders in this timing section twice as fast as `SliderMultiplier`.
- **`meter` (Integer):** Amount of beats in a measure. Inherited timing points ignore this property.
- **`sampleSet` (Integer):** Default sample set for hit objects (0 = beatmap default, 1 = normal, 2 = soft, 3 = drum).
- **`sampleIndex` (Integer):** Custom sample index for hit objects. `0` indicates osu!'s default hitsounds.
- **`volume` (Integer):** Volume percentage for hit objects.
- **`uninherited` (0 or 1):** Whether or not the timing point is uninherited.
- **`effects` (Integer):** Bit flags that give the timing point extra effects. See [the effects section](#effects).

### Effects

Timing points have two extra effects that can be toggled using bits 0 and 3 (from least to most significant) in the `effects` integer:

- 0: Whether or not [kiai time](/wiki/Beatmap_Editor/Kiai_Time) is enabled
- 3: Whether or not the first barline is omitted in osu!taiko and osu!mania

The rest of the bits are unused.

### Examples

```
10000,333.33,4,0,0,100,1,1
12000,-25,4,3,0,100,0,1
```

The first timing point at 10 seconds is uninherited, and sets:

- BPM to 180 (`1 / 333.33 * 1000 * 60`)
- Time signature to 4/4
- Sample set to the beatmap default
- Sample index to osu!'s default hitsounds
- Volume to 100%
- Kiai time

The second timing point at 12 seconds is inherited, changing the slider velocity to 4x and the sample set to drum.

## Colours

All options in this section represent colours. They are comma-separated triplets of integers 0–255, representing the red, green, and blue components of the colors.

| Option | Description |
| :-- | :-- |
| `Combo#`, where `#` is an integer | Additive combo colours |
| `SliderTrackOverride` | Additive slider track colour |
| `SliderBorder` | Slider border colour |

## Hit objects

*Hit object syntax:* `x,y,time,type,hitSound,objectParams,hitSample`

- **`x` (Integer)** and **`y` (Integer):** Position in [osu! pixels](/wiki/Glossary#osupixel) of the object.
- **`time` (Integer):** Time when the object is to be hit, in milliseconds from the beginning of the beatmap's audio.
- **`type` (Integer):** Bit flags indicating the type of the object. See [the type section](#type).
- **`hitSound` (Integer):** Bit flags indicating the hitsound applied to the object. See [the hitsounds section](#hitsounds).
- **`objectParams` (Comma-separated list):** Extra parameters specific to the object's type.
- **`hitSample` (Colon-separated list):** Information about which samples are played when the object is hit. It is closely related to `hitSound`; see [the hitsounds section](#hitsounds). If it is not written, it defaults to `0:0:0:0:`.

### Type

Hit object types are stored in an 8-bit integer where each bit is a flag with special meaning. The base hit object type is given by bits 0, 1, 3, and 7 (from least to most significant):

- 0: Hit circle
- 1: Slider
- 3: Spinner
- 7: osu!mania hold

The remaining bits are used for distinguishing new combos and optionally skipping combo colours (commonly called "colour hax"):

- 2: New combo
- 4–6: A 3-bit integer specifying how many combo colours to skip, if this object starts a new combo.

### Hitsounds

The `hitSound` bit flags determine which sounds will play when the object is hit:

- 0: Normal
- 1: Whistle
- 2: Finish
- 3: Clap

If no bits are set, the normal hitsound is used by default.

In every mode except osu!mania, the `LayeredHitSounds` skin property forces the normal sound to be included regardless of bit 0's setting. It is enabled by default.

#### Custom hit samples

Usage of `hitSample` can further customize the sounds that play. It defaults to `0:0:0:0:` if it is not written.

*Hit sample syntax:* `normalSet:additionSet:index:volume:filename`

- **`normalSet` (Integer):** Sample set of the normal sound.
- **`additionSet` (Integer):** Sample set of the whistle, finish, and clap sounds.
- **`index` (Integer):** Index of the sample. If this is `0`, the timing point's sample index will be used instead.
- **`volume` (Integer):** Volume of the sample from 1 to 100. If this is `0`, the timing point's volume will be used instead.
- **`filename` (String):** Custom filename of the addition sound.

`normalSet` and `additionSet` can be any of the following:

- `0`: No custom sample set
  - For normal sounds, the set is determined by the timing point's sample set.
  - For additions, the set is determined by the normal sound's sample set.
- `1`: Normal set
- `2`: Soft set
- `3`: Drum set

All of these options (besides volume) are used to determine which sound file to play for a given hitsound. The filename is `<sampleSet>-hit<hitSound><index>.wav`, where:

- `sampleSet` is `normal`, `soft`, or `drum`, determined by either `normalSet` or `additionSet` depending on which hitsound is playing
- `hitSound` is `normal`, `whistle`, `finish`, or `clap`
- `index` is the same `index` as above, except it is not written if the value is `0` or `1`

The sound file is loaded from the first of the following directories that contains a matching filename:

- Beatmap, if `index` is not `0`
- Skin, with the `index` removed
- Default osu! resources, with the `index` removed

When `filename` is given, no addition sounds will be played, and this file in the beatmap directory is played instead.

### Hit circles

Hit circles do not have additional `objectParams`.

### Sliders

*Slider syntax:* `x,y,time,type,hitSound,curveType|curvePoints,slides,length,edgeSounds,edgeSets,hitSample`

- **`curveType` (Character):** Type of curve used to construct this slider (`B` = bézier, `C` = centripetal catmull-rom, `L` = linear, `P` = perfect circle)
- **`curvePoints` (Pipe-separated list of strings):** Points used to construct the slider. Each point is in the format `x:y`.
- **`slides` (Integer):** Amount of times the player has to follow the slider's curve back-and-forth before the slider is complete. It can also be interpreted as the repeat count plus one.
- **`length` (Decimal):** Visual length in [osu! pixels](/wiki/Glossary#osupixel) of the slider.
- **`edgeSounds` (Pipe-separated list of integers):** Hitsounds that play when hitting edges of the slider's curve. The first sound is the one that plays when the slider is first clicked, and the last sound is the one that plays when the slider's end is hit.
- **`edgeSets` (Pipe-separated list of strings):** Sample sets used for the `edgeSounds`. Each set is in the format `normalSet:additionSet`, with the same meaning as in [the hitsounds section](#hitsounds).

#### Slider curves

When constructing curves for a slider, `x` and `y` are used for the first point, and `curvePoints` supply the rest.

There are four types of slider curves in osu!:

- **Bézier (B):** [Bézier curves](https://en.wikipedia.org/wiki/Bézier_curve) of arbitrary degree can be made. Multiple bézier curves can be joined into a single slider by repeating their points of intersection.
- **Centripetal catmull-rom (C):** [Catmull curves](https://en.wikipedia.org/wiki/Centripetal_Catmull–Rom_spline) are an interpolating alternative to bézier curves. They are rarely used today due to their lack of visual appeal.
- **Linear (L):** These curves form a straight path between all of their points.
- **Perfect circle (P):** Perfect circle curves are limited to three points (including the hit object's position) that define the boundary of a circle. Using more than three points will result in the curve type being switched to bézier.

If the slider's `length` is longer than the defined curve, the slider will extend until it reaches the target length:

- For bézier, catmull, and linear curves, it continues in a straight line from the end of the curve.
- For perfect circle curves, it continues the circular arc.

*Notice: The slider's `length` can be used to determine the time it takes to complete the slider. `length / (SliderMultiplier * 100) * beatLength` tells how many milliseconds it takes to complete one slide of the slider (assuming `beatLength` has been adjusted for inherited timing points).*

#### Slider hitsounds

Apart from edge hitsounds, sliders also have an ongoing hitsound whenever the player is in range of the slider's follow circle. The sound file is looped for as long as it is active.

This hitsound uses the hit object's `hitSound` and `hitSample` properties, but only the normal and whistle sounds are supported. Its filename is `<sampleSet>-hit<hitSound><index>.wav`, where `hitSound` is either `slide` for normal or `whistle` for whistle.

### Spinners

*Spinner syntax:* `x,y,time,type,hitSound,endTime,hitSample`

- **`endTime` (Integer):** End time of the spinner, in milliseconds from the beginning of the beatmap's audio.
- `x` and `y` do not affect spinners. They default to the centre of the playfield, `256,192`.

### Holds (osu!mania only)

*Hold syntax:* `x,y,time,type,hitSound,endTime:hitSample`

- **`endTime` (Integer):** End time of the hold, in milliseconds from the beginning of the beatmap's audio.
- `x` determines the index of the column that the hold will be in. It is computed by `floor(x * columnCount / 512)` and clamped between `0` and `columnCount - 1`.
- `y` does not affect holds. It defaults to the centre of the playfield, `192`.

### Examples

```
256,192,11000,21,2
256,192,11200,8,12,12000,3:0:0:80:
100,100,12600,6,1,B|200:200|250:200|250:200|300:150,2,310.123,2|1|2,0:0|0:0|0:2,0:0:0:0:
```

The first object is a hit circle:

- In the centre of the screen
- At 11 seconds
- Starting a new combo, and skipping one extra combo colour
- With a whistle hitsound

The second object is a spinner:

- At 11.2 seconds
- Ending at 12 seconds
- With finish and clap hitsounds, playing at 80% volume
- With the normal hitsound playing with the drum set, at 80% volume

The third object is a slider:

- At the position (100,100)
- At 12.6 seconds
- Starting a new combo
- With a compound bézier curve slider body, where the first curve's control points are (100,100), (200,200), and (250,200), and the second curve's control points are (250,200), (300,150)
- Repeating once
- 310.123 osu! pixels long
- With a whistle hitsound at the beginning, and a whistle hitsound playing with the soft set at the end

<!-- TODO: specific details about all of the other game modes (this article should provide everything necessary to parse a .osu file)

also there is no info about how they convert to other game modes from an osu!standard beatmap -->

### osu!taiko

osu!taiko's hit objects only use `time` to determine how they are placed on the play field, so `x` and `y` are ignored. Likewise, the only significant part of slider curves is `length`; `curveType` and `curvePoints` are only relevant when opening the map in the editor. Combo colours and new combos are ignored, and mode-specific hitsounds are used.

- Hit circles with whistle or clap hitsounds become kats, and other hit circles become dons. Adding the finish hitsound changes these into their large variants.
- Sliders become drum rolls.
- Spinners become denden notes.

### osu!catch

osu!catch's play field only uses the x-axis, so `y` is not relevant. Slider curves may utilize vertical space to achieve horizontal acceleration when they are flattened to a one-dimensional play field.

- Hit circles become fruits.
- Sliders become juice streams, with fruits on each edge.
- Spinners become banana showers

### osu!mania

Similarly to osu!catch, osu!mania hit objects do not use `y`. `x` is used to determine the column; see the [Holds section](#holds-(osu!mania-only)).

- Hit circles become normal notes.
- Sliders and spinners are not used in osu!mania.
