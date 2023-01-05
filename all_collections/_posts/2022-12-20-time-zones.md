---
layout: post
title: Часовые пояса
date: 2022-12-20
categories: ["Swift", "SPL"]
---

# Часовые пояса

До введения системы часовых поясов в каждом населённом пункте использовалось своё местное солнечное время, определяемое географической долготой конкретного населённого пункта или ближайшего крупного города. Система стандартного времени появилась в конце XIX века. Её необходимость стала особенно актуальной с развитием сети железных дорог — если графики движения поездов составлялись по местному солнечному времени каждого города, то это могло вызвать не только неудобства и путаницу, но и аварии. Первые проекты стандартизации времени появились и были реализованы в Великобритании.

Идею мировой системы часовых поясов одним из первых представил итальянский математик Квирико Филопанти в своей книге «Miranda» в 1859 году. Он предложил разделить поверхность Земли по долготе вдоль меридианов на 24 зоны, отличающиеся друг от друга на один час с точным совпадением минут и секунд. Первая часовая зона находилась на меридиане Рима и включала Италию, Германию, Швецию и часть Африки. Филопанти предложил также использовать универсальное (всемирное) время в астрономии и телеграфии.

## Понятие часово́й по́яс

Понятие часово́й по́яс имеет два основных значения:

- **Географи́ческий часовой пояс** — условная полоса на земной поверхности шириной ровно `15°` (`±7,5°` относительно среднего меридиана). Средним меридианом нулевого часового пояса считается *гринвичский меридиан*.
- **Администрати́вный часовой пояс** — участок земной поверхности, на котором в соответствии с некоторым законом установлено определённое официальное время. Как правило, в понятие административного часового пояса включается ещё и совпадение даты — в этом случае, например, пояса `UTC−10:00` и `UTC+14:00` будут считаться различными, хотя в них действует одинаковое время суток.

Формирование часовых поясов (часовых зон — time zones) связано со стремлением, с одной стороны, учитывать вращение Земли вокруг своей оси, а с другой стороны, определить территории (временные зоны) с примерно одинаковым местным солнечным временем таким образом, чтобы различия по времени между ними были кратны одному часу. В результате было достигнуто решение, что должно быть 24 административных часовых пояса и каждый из них должен более или менее совпадать с географическим часовым поясом. За точку отсчёта был принят гринвичский меридиан — **нулевой меридиан**, который проходит через Гринвичскую обсерваторию в пригороде Лондона. Отсчёт часовых поясов происходит с Запада на Восток. При перемещении на запад от нулевого меридиана, стрелка часов перемещается вперёд, при перемещении на Восток – назад. Линия перемены дат проходит на карте мира между Россией и США.

Сейчас поясное время устанавливается относительно **всемирного координированного времени (UTC)**, введённого взамен **времени по Гринвичу (GMT)**. Шкала UTC базируется на равномерной шкале атомного времени (TAI) и более удобна для гражданского использования. Часовые пояса относительно нулевого меридиана выражаются как положительное (к востоку) и отрицательное (к западу) смещение от UTC. Для территорий часового пояса, где используется перевод часов на летнее время, смещение относительно UTC на летний период меняется.

### Принципы разграничения

В основу современной системы часовых поясов положено всемирное координированное время, от которого зависит время всех поясов. Чтобы не вводить местное солнечное время для каждого значения долготы, поверхность Земли условно поделена на **24 часовых пояса**, местное время на границах которых изменяется ровно на 1 час. Географические часовые пояса ограничиваются меридианами, проходящими на `7,5°` восточнее и западнее среднего меридиана каждого пояса, причём в зоне гринвичского меридиана действует всемирное время. Однако в реальности, для сохранения единого времени в пределах одной административной территории или группы территорий, границы поясов не совпадают с теоретическими граничными меридианами.

Реальное количество часовых поясов больше 24, так как в ряде стран правило целочисленной разницы в часах от всемирного времени нарушается — местное время кратно получасу или четверти часа. Кроме того, вблизи линии перемены даты в Тихом океане есть территории, использующие время дополнительных поясов: +13 и даже +14 часов.

Местами некоторые часовые пояса пропадают — время этих поясов не используется, что характерно для малонаселённых регионов, находящихся выше широты приблизительно 60°, например: Аляска, Гренландия, северные регионы России. На Северном и Южном полюсах меридианы сходятся в одной точке, поэтому там понятия часовых поясов и местного солнечного времени теряют смысл. Например, на станции Амундсен-Скотт (Южный полюс) действует время Новой Зеландии.

### Летнее время

Дополнительную неоднозначность в систему часовых поясов вносит использование во многих странах летнего времени. При переходе на летнее время происходит смещение своего времени относительно всемирного. При этом не везде переход на летнее время и обратно осуществляется одновременно. Кроме того, если в южном полушарии лето, то в северном полушарии зима, и наоборот.

## Среднее время по Гринвичу

**Сре́днее вре́мя по Гри́нвичу** (англ. Greenwich Mean Time, GMT), или гри́нвичское время — среднее солнечное время меридиана, проходящего через прежнее место расположения Гринвичской королевской обсерватории около Лондона.

Ранее, до 1972 года, гринвичское время, GMT, считалось точкой отсчёта времени в других часовых поясах. Сейчас в этом качестве используется всемирное координированное время (UTC).

Иногда в русскоязычной метрологии GMT обозначают как ГСВ, расшифровывая это как «гринвичское (или географическое) среднее время».

## Всемирное координированное время

**Всеми́рное координи́рованное вре́мя** (англ. Coordinated Universal Time, фр. Temps Universel Coordonné; UTC) — стандарт, по которому общество регулирует часы и время. Отличается на целое количество секунд от атомного времени и на дробное количество секунд от всемирного времени UT1.

UTC было введено вместо устаревшего среднего времени по Гринвичу (GMT), поскольку шкала GMT является неравномерной и связана с суточным вращением Земли. В свою очередь, шкала UTC основана на равномерной шкале атомного времени (TAI) и является более удобной для гражданского использования.

Время по UTC не переводится ни зимой, ни летом. Поэтому для тех мест, где есть переход на летнее время, меняется смещение относительно UTC. Часовые пояса вокруг земного шара выражаются как положительное или отрицательное смещение от UTC.

### UTC и другие системы измерения времени

Аббревиатура UTC не имеет конкретной расшифровки. Когда в 1970 году требовалось создать не зависящее от языка сокращение, Международный союз электросвязи счёл, что английское *CUT — Coordinated Universal Time* или французское *TUC — Temps Universel Coordonné* не подходят на эту роль. Поэтому был предложен нейтральный вариант — **UTC**.

Всемирное время UT является современной версией *среднего времени по Гринвичу*, то есть среднего солнечного времени на Гринвичском меридиане. Из-за неравномерности вращения Земли Гринвичский меридиан вращается также неравномерно. Кроме того, в результате непрерывного перемещения оси вращения в теле самой Земли географические полюса смещаются по поверхности Земли, а вместе с ними изменяют своё положение и плоскости истинных меридианов. Из-за этих факторов различают следующие системы измерения времени:

- **UT0** — время на мгновенном гринвичском меридиане, определённое по мгновенному положению полюсов Земли. Это время, непосредственно получаемое из астрономических наблюдений суточных движений звёзд;
- **UT1** — время на среднем гринвичском меридиане, учитывающее движение земных полюсов (по сути, современная версия среднего времени по Гринвичу):

	`UT1 = UT0 + Δλ,`

	где Δλ — поправка, зависящая от координат мгновенного полюса, отсчитываемых относительно общепринятого среднего полюса;
- **UT2** — время, исправленное на сезонную неравномерность вращения Земли ΔTs:

	`UT2 = UT1 + ΔTs`.

Шкала наблюдаемого всемирного времени UT1, из-за её неравномерности, неудобна для использования в гражданской жизни. Поэтому с 1964 года ввели равномерно-переменную шкалу времени UTC — всемирного координированного времени, связывающую шкалу UT1 и шкалу строго равномерного Международного атомного времени (TAI). Масштабы UTC и TAI равны, а нульпункт меняется скачком. Между UTC и UT1 накапливается расхождение, обусловленное, во-первых, неравномерностью шкалы UT1, а во-вторых, неравенством масштабов UT1 и TAI (1 атомная секунда не равна в точности 1 секунде UT1). При нарастании расхождения между UTC и UT1 до 0,9 с производится корректировка скачком на 1 с.

Дополнительная секунда при необходимости добавляется 30 июня или 31 декабря после `23:59:59`. Теоретически может потребоваться и вычитание секунды, но пока, начиная с первого изменения — 30 июня 1972 года, были только вставки дополнительной секунды. Добавлению секунды соответствует отображение текущего времени `23:59:60`. Добавление секунды определяется *Международной службой вращения Земли (IERS)*, согласно их наблюдению за вращением планеты.

Сигналы точного времени передаются по радио, телевидению и через Интернет в системе **UTC**.

Разница между всемирным временем и всемирным координированным временем `DUT1 = UT1 − UTC` постоянно отслеживается и ежедневно публикуется на сайте IERS на основании данных "Бюллетеня А" (Bulletin — A).

## Использование 

Часовые пояса по всему миру выражаются с использованием положительных или отрицательных смещений по UTC. Самый западный часовой пояс использует UTC−12, отставая на 12 часов, а самый восточный часовой пояс использует UTC+14, опережая UTC на четырнадцать часов. В 1995 году островное государство Кирибати перенесло свои атоллы на Лайнских островах с UTC−10 на UTC+14, чтобы в календарях всех островов Кирибати был один и тот же день.

UTC используется во многих стандартах Интернета. Протокол сетевого времени (NTP), предназначенный для синхронизации часов компьютеров через Интернет, передаёт информацию о времени от системы UTC. Если требуется точность только в миллисекундах, клиенты могут получить текущий UTC с нескольких официальных интернет-серверов UTC. Для точности до микросекунд клиенты могут получать время от спутников.

UTC также является стандартом времени, используемым в авиации, например, для планов полёта и управления воздушным движением. Прогнозы погоды и карты используют UTC, чтобы избежать путаницы с часовыми поясами и переходом на летнее время. Международная космическая станция использует UTC в качестве эталона времени.

На изображении представлены часовые пояса по странам. Наибольшее количество часовых поясов имеет Франция (в совокупности территорий) — 12. В ряде стран применяется летнее время, когда на летний период прибавляется один час, но на данном изображении эти сведения не представлены.

![Карта временных зон](https://obodev.github.io/assets/images/time-zones-map.png "Карта временных зон")

В качестве сокращённого обозначения часовых зон в списке использованы некоторые принятые английские аббревиатуры, для которых даются соответствующие русскоязычные названия:

| Обозначение | Наименование                           | Часовой пояс |
|:------------|:---------------------------------------|:-------------|
| ACST        | центральноавстралийское время          | UTC+9:30     |
| AEST        | восточноавстралийское время            | UTC+10       |
| AKST        | аляскинское время                      | UTC−9        |
| AST         | атлантическое время                    | UTC−4        |
| AWST        | западноавстралийское время             | UTC+8        |
| CAT         | центральноафриканское время            | UTC+2        |
| CET         | центральноевропейское время            | UTC+1        |
| CST         | центральноамериканское время           | UTC−6        |
| EAT         | восточноафриканское время              | UTC+3        |
| EET         | восточноевропейское время              | UTC+2        |
| EST         | североамериканское восточное время     | UTC−5        |
| GMT         | среднее время по Гринвичу              | UTC          |
| HAST        | гавайско-алеутское время               | UTC−10       |
| MSK         | московское время                       | UTC+3        |
| MST         | горное время                           | UTC−7        |
| NST         | ньюфаундлендское время                 | UTC−3:30     |
| PST         | североамериканское тихоокеанское время | UTC−8        |
| UTC         | всемирное координированное время       | UTC          |
| WAT         | западноафриканское время               | UTC+1        |
| WET         | западноевропейское время               | UTC          |

## Часовые пояса в разных странах

На территории (территориях) некоторых стран мира применяется время нескольких часовых поясов. Некоторые страны расположены во многих часовых поясах за счёт островных и заморских территорий, например:

- Великобритания с заморскими территориями — 8 часовых поясов.
- США с островными территориями (Американское Самоа, Мидуэй, Виргинские Острова (США), Пуэрто-Рико и т. д.) — 11 часовых поясов.
- Франция с заморскими департаментами и прочими территориями (Сен-Пьер и Микелон, Мартиника, Гваделупа, Французская Гвиана, Майотта, Реюньон, Южно-антарктические территории, Новая Каледония, Валлис и Футуна, Французская Полинезия, Клиппертон и ряд других обитаемых и необитаемых островов) — 12 часовых поясов.

Территории большинства стран (включая Францию и Великобританию без их заморских владений и территорий) расположены в одном часовом поясе. Некоторые значительно протяжённые по долготе страны тоже применяют время одного часового пояса. Например, территория Китая расположена в пяти географических часовых поясах, но на всей его территории действует единое Китайское стандартное время.

В некоторых странах на территории административно-территориальных единиц применяется время двух или более часовых поясов. Например, время трёх часовых поясов использует Республика Саха (Якутия), являющаяся субъектом Российской Федерации, и канадская территория Нунавут.

В США и Канаде границы часовых поясов часто разделяют штат, провинцию или территорию, поскольку территориальная принадлежность к тому или иному поясу определяется на уровнях административно-территориальных единиц второго порядка (графства или округа).

---

## Еще полезные ссылки