<style lang="scss">
.image-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 40px;
}
</style>

# Как выбрать аппаратуру радиоуправления?

> Авторы: [Андрей Щ.](https://github.com/EIIIE), [Валентина](https://github.com/ikherty)

## Резюме

Аппаратура Радиоуправления (она же Аппаратура РУ, transmitter, пульт, аппа, джойстик) - устройство, преобразующее положения стиков (gimbals)/тумблеров (switches) в команды для коптера.
Положение стиков отправляются на радиопередатчик (transmitter, tx, в аппаратуре), преобразующий сигналы в команды определенного протокола передачи данных. Команды передаются коптеру "по воздуху" на определенной частоте (обычно 900 МГЦ или 2.4 ГГЦ). На борту коптера команды принимает радиоприемник (receiver, rx) и отправляет их на полетный контроллер (flight controller, FC) для исполнения.

<p class="image-container">
  <img src="/assets/img/tx-rx.webp" width="600" alt="Связь между аппаратурой и дроном" title="Связь между аппаратурой и дроном">
</p>

## Протоколы передачи данных

Немаловажный момент в выборе радиолинка (RC Link) - протокол, по которому команды передаются на дрон.

В 2023 году наиболее популярными радио системами являются:

**TBS Crossfire** - дальнобойная система, работающая на частоте 900 МГц. Позволяет ставить рекорды в сотни километров при соблюдении определенного ряда условий (локация, тип ЛА, настройки передатчика, расположение антенн и многое другое).
Встречается в качестве внешних передатчиков разных формфакторов и в качестве встроенного модуля аппаратуры [TBS Tango 2](https://www.team-blacksheep.com/products/prod:tbs_tango_2).

Плюсы и минусы TBS Crossfire:

- На первый взгляд, user friendly программное обеспечение для настройки и обновления прошивки. Очень подробная документация, отзывчивая поддержка. Однако при выходе новых версий периодически возникают проблемы с коннектом, о которых в явном виде можно узнать только по чатам или на личном опыте.
- В теории, при идеальных условиях, управление с помощью этой системы будет еще некоторое время оставаться после обрыва видеосвязи. Поскольку частота ниже и длина волны больше, чем у стандартных радиопротоколов на 2,4 ГГц и самой распространенной видеосвязи на частоте 5,8 ГГц. Но это не гарантирует, что вы никогда не потеряете связь с аппаратурой до проблем с видео.
- Система является закрытой, достаточно сложно убедить производителя что-либо исправить или самому доработать.
- Не подходит для гонок на профессиональном уровне из-за ощутимых (для топ пилотов) задержек передачи команд, так как работает на частоте 900 МГЦ. В целом, антенны приемников достаточно габаритные, это не прибавляет удобств.
- Дорого в сравнении с некоторыми аналогами, поскольку особо нет конкурентов в том же сегменте.
- При packet rate в 150Гц работает на меньших дистанциях при той же мощности передатчика, что и ELRS 2.4 на packet rate 150-250Гц
- Подойдет любителям ставить рекорды на дальность и летать в сложных условиях.

[**ELRS (он же ExpressLRS - Express Long Range System)**](https://www.expresslrs.org/) - система, созданная самим сообществом. Есть версия на 900 МГц и 2,4 ГГц. Рекомендуется версия на 2,4 ГГЦ. Встречаются в качестве внешних передатчиков разных формфакторов и в качестве встроенного модуля аппаратур от radiomaster, jumper и других (менее популярных).

Плюсы и минусы ELRS:

- Коды и схемы в открытом доступе, что мотивировало производителей железа выпускать приемники, передатчики, полетные контроллеры со встроенным приемником, и появилась высокая конкуренция. Как результат - лучший вариант по соотношению цена/качество, самое актуальное железо по минимальной цене.
- Дальность передачи команд легко превышает дальность работы видеопотока (умельцы летают десятки километров, на данный момент рекорд 100 км, посмотреть таблицу с тестами можно здесь: https://www.expresslrs.org/2.0/info/long-range)
- Минимальные задержки передачи данных, поскольку можно выбрать частоту отправки пакетов вплоть до 500 Гц -> отлично подходит для гонок (но учтите, что дальность при этом уменьшается).
- Среди доступных на рынке приемников есть линейка самых легких и компактных (см. [happymodel ep2](https://www.happymodel.cn/index.php/2021/04/10/happymodel-2-4g-expresslrs-elrs-nano-series-receiver-module-pp-rx-ep1-rx-ep2-rx/)).
- Программное обеспечение постепенно улучшается, упрощается для пользователя. Документация также обширна и подробна. Для избежания проблем с прошивками рекомендуется брать наиболее популярное железо с наименьшим количеством "косяков" за время роста проекта (например, happymodel). Про косяки можно спросить в чатах и у сообщества.
- Новое железо от производителей появляется каждый месяц и разработчики не всегда успевают выпускать софт для них или исправлять ошибки. Поэтому надо быть готовым к тому, что с некоторыми платами придется подождать прошивок или исправлений. Если вы нашли проблему, можете сообщить о ней или поискать по ключевым словам в [репозитории ExpressLRS](https://github.com/ExpressLRS/ExpressLRS) заведенные заявки (issues) и обязательно получите решение в ближайшее время. Также есть сайт с переводом на русский язык и описанием ключевых моментов по прошивкам, настройкам - http://expresslrs.ru/ и чат, где всегда подскажут (ссылка на чат на сайте).

Конкуренты ELRS, но с закрытыми прошивками:

[**TBS Tracer**](https://www.team-blacksheep.com/tracer/) - если кратко: "натянули Crossfire на гонщиков". Работает на 2,4 ГГЦ (Crossfire медленнее - 900 МГц), по удобству схож с ним. Не такой быстрый как ELRS, не такой дальнобойный как Crossfire, первое время были проблемы с дальностью. Cо временем вышли новые прошивки с исправлением, но все еще имеет место быть. Встречается в виде отдельного модуля и в качестве встроенного передатчика аппаратуры [TBS Mambo](https://www.team-blacksheep.com/products/prod:tbs_mambo).

[**IMMERSION RC GHOST**](https://www.immersionrc.com/fpv-products/ghost/) - соперник ELRS по минимизации задержек передачи команд. Наиболее распространен в штатах, вероятно, ввиду доступности. В основном используется топ гонщиками. Встречается только в качестве внешнего передатчика.

> Устаревшее и что **не стоит брать** с 2020 года для дронов: frsky, flysky, dsmx (spektrum)...

Как правило, новичкам рекомендуется начинать с ELRS - дешевый и доступный вход. Но если не важна задержка и планируется в основном Long Range на различных сложных локациях - можно посмотреть в сторону TBS Crossfire.

Подробно про протоколы - https://oscarliang.com/rc-protocols/ (английский язык)

## Передатчик и приемник

Аппаратура и коптер общаются между собой при помощи передатчика и приемника.
Передатчик в аппаратуре может быть как встроенным (распаянным на плате), так и внешним (вставляющимся в слот на задней части аппаратуры). Встроенный модуль, как правило, удобнее ввиду компактности, в некоторых случаях потребляет меньше питания, чем внешний. Максимальная мощность внешнего передатчика может быть ограничена 250мВт. Однако этого достаточно даже для 50 км. Если глянуть [таблицу с тестами на сайте ELRS](https://www.expresslrs.org/software/switch-config/), то в некоторых случаях может быть мало.

> Ниже представлены аппаратура без кожуха и внешний модуль ELRS. На плате можно найти модуль-передачтик. Внешний же модуль-передатчик устанавливается в специальный разъём снаружи аппаратуры

<style>
  .img-inline {
    display: grid;
    grid-template-columns: 3fr 1fr;
    grid-auto-rows: minmax(250px, 340px);
    gap: 0px 5px;
    padding: 0;
    align-items: center;
    justify-items: center;
  }
  .left {
    grid-column: 1;
    grid-row: 1;
  }
  .right {
    grid-column: 2;
    grid-row: 1;
  }
</style>

<p class="img-inline">
  <img class="left" style="height: 340px;" src="/assets/img/TBS-Mambo-Tracer-module-and-PCB-antenna-picture-by-LIVYU-768x520.jpg" alt="Аппаратура без кожуха" title="Аппаратура без кожуха">
  <img class="right" style="height: 340px;" src="/assets/img/happy-odel-2_4ghz-es24tx.webp" alt="Внешний модуль ELRS" title="Внешний модуль ELRS">
</p>

Приемник - это небольшая плата с антенной(ами), устанавливающаяся на дрон и подключающаяся к его полетному контроллеру на [UART (Universal Asynchronous Receiver-Transmitter, универсальный асинхронный приёмопередатчик)](https://ru.wikipedia.org/wiki/%D0%A3%D0%BD%D0%B8%D0%B2%D0%B5%D1%80%D1%81%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D0%B0%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%BD%D1%8B%D0%B9_%D0%BF%D1%80%D0%B8%D1%91%D0%BC%D0%BE%D0%BF%D0%B5%D1%80%D0%B5%D0%B4%D0%B0%D1%82%D1%87%D0%B8%D0%BA).

> Ниже представлены приемник Happymodel EP2 ELRS с керамической антенной и приемник Ghost с диполь антенной

<p class="image-container">
    <img style="height: 300px" src="/assets/img/EP2_RX1.webp" alt="Приемник Happymodel ELRS 2.4GHz" title="Приемник Happymodel ELRS 2.4GHz">
    <img style="height: 300px" src="/assets/img/immersion-rc-ghost-atto-reciever.webp" alt="Приемник Ghost" title="Приемник Ghost">
</p>

**Не важны различия в производителях передатчика и приемника, пока они оба работают на одном протоколе. Но если речь идет про ELRS, лучше изучить рекомендации и тесты железа разных производителей.**

## Выбор аппаратуры

Обновляемая статья на английском языке про аппаратуры, достойная внимания - https://oscarliang.com/radio-transmitter/

Краткий перечень на английском языке без "воды" - https://www.fpvknowitall.com/fpv-shopping-list-controller-and-receiver/

Если в статьях выше нет аппаратуры, которая вас интересует, то либо она слишком новая, либо мало предпочитаемая сообществом.

## Рекомендуемые аппаратуры

Настоятельно рекомендуется рассматривать аппаратуры, работающие на ПО OpenTX (потомком которого является EdgeTX). Это как операционная система компьютера. С ним ты будешь уверен, что спокойно подключишь к симулятору и будешь продолжать получать обновления с новыми фишками.

[**RADIOMASTER TX16S**](https://www.radiomasterrc.com/products/tx16s-mark-ii-radio-controller) - Если у тебя большие руки, нужно много свитчей (переключателей, тумблеров, потов/крутилок), хочется (зачем-то) большой экран.

Цены обычно от 200$, есть версии со встроенным ELRS (внимательно читайте описание, не путайте с мультимодулем (4in1, cc2500), который не включает в себя ELRS и Crossfire). Можно поставить внешний передатчик по вкусу (30-250$). Существует в различных модификациях - цветные корпусы, алюминиевые стики, с тачскрином. Дополнительно разноцветные моды есть, в целом, у всех аппаратур от radiomaster.

<p class="image-container">
  <img src="/assets/img/tx16s.webp" height="400" alt="Аппаратура RADIOMASTER TX16S" title="Аппаратура RADIOMASTER TX16S">
</p>

[**RADIOMASTER BOXER**](https://www.radiomasterrc.com/products/boxer-radio-controller-m2?_pos=1&_sid=194aad403&_ss=r) - Средний вариант по габаритам с полноразмерными стиками, достаточным количеством свитчей даже для самолетчиков.

Цена 130-160$ в зависимости от версии, есть вариант со встроенным ELRS модулем на 1Вт и мультимодулями, в прозрачном или черном корпусе. Для питания необходимы 2 lion 18650, но также вместится и 2s из 21700. Считается компромисом между tx16 и компактными вариантами, которые ниже по списку. Подойдет большинству начинающих и не только.

<p class="image-container">
  <img src="/assets/img/BOXER.webp" height="400" alt="Аппаратура RADIOMASTER Boxer" title="Аппаратура RADIOMASTER Boxer">
</p>

[**RADIOMASTER TX12 mk2**](https://www.radiomasterrc.com/products/tx12-mark-ii-radio-controller?_pos=1&_sid=02bbb6530&_ss=r) - Компактная версия "кирпичика" с мини версией стиков.

Цены обычно от 80$, есть версии со встроенным ELRS (внимательно читайте описание). Отдельно можно приобрести цветные корпусы, алюминиевые стики. Для питания необходимы 2 lion 18650. Также неплохой вариант для начала, когда не понятно, что хочется, и нужна компактность. Легко будет продать в любой момент на барахолке, если по какой-либо причине "не зайдет".

<p class="image-container">
  <img src="/assets/img/tx12.webp" height="400" alt="Аппаратура RADIOMASTER TX12" title="Аппаратура RADIOMASTER TX12">
</p>

[**RADIOMASTER Pocket**](https://www.radiomasterrc.com/collections/transmitter/products/pocket-radio-controller-m2) - Упрощенная полноценная версия аппаратуры в "карманном" варианте с откосом под танго.

Цены от 54$, есть версии со встроенным ELRS (внимательно читайте описание). Стики минимального размера, пока что нет возможности заменить на более качественные. Отдельно можно приобрести цветные корпусы. К сожалению, производитель поставил только кнопки и ни единого тумблера в угоду компактности. Для кого-то это не проблема, но все же [большинство предпочитает](https://t.me/propwash/304) для арма использовать тумблер, поскольку это более быстрый способ арма/дизарма и надежнее кнопки. Есть возможность установить внешний передатчик. Для питания необходимы 2 lion 18650. Неплохой вариант для самого бюджетного комплекта, когда не понятно, что хочется, и нужна компактность. Свежая новинка, неизвестно, какие проблемы стоит ожидать.

<p class="image-container">
  <img src="/assets/img/POCKET.webp" height="400" alt="Аппаратура RADIOMASTER TX12" title="Аппаратура RADIOMASTER Pocket">
</p>

[**TBS TANGO 2**](https://www.team-blacksheep.com/products/prod:tbs_tango_2) - Компактный вариант со строенным crossfire передатчиком. Подходит, если цель путешествовать налегке. Не путать с первой версией :)

Есть обычная версия за 160$ и pro за 200$. В России цены от 20 тыс. руб., продавцы объсняют такую разницу сложностями поставок. Основное отличие pro версии в складывающихся стиках, но явного преимущества в этом нет. Встроенный передатчик TBS CROSSFIRE, мощность зависит от версии платы. При особой любви и необходимости можно установить внешний передатчик. Также есть вариант встроить ELRS модуль с небольшой мощностью для полетов неподалеку, как [в этом видео](https://www.youtube.com/watch?v=2cn96u_nlnw). Крайне маленький экран, но для полетов в режиме FPV он и не нужен. Кнопки вместо тумблеров - дело на любителя, но не всегда получается моментально "задизармить" коптер (то есть выключить моторы). Бывают проблемы со стиками: поскольку используется "супер технология" с одним датчиком на 2 оси, калибровку надо производить строго по инструкции производителя. Сами стики "разведены" на материнской плате, поэтому нет возможности легко заменить их на другие, как в случае с аппаратурами Radiomaster. Иногда бывают проблемы с глюками экрана, "окирпичиванием" модуля при прошивке, требованием калибровки при запуске. Но, несмотря на это, все еще пользуется популярностью.

<p class="image-container">
  <img src="/assets/img/tango2.webp" height="400" alt="аппаратура TBS Tango 2">
</p>

[TBS Mambo](https://www.team-blacksheep.com/products/prod:tbs_mambo) - Типовой кирпичик для фанатов TBS Tracer

140$, в России часто от 18 тыс. руб.. Встроенный передатчик TBS Tracer. У аппаратуры достаточное количество свитчей, полноценный черно-белый экран, есть слот под внешний передатчик. Есть мнение, что с mambo срисован RadioMaster Boxer - формфактор практически идентичен, расположение свитчей схоже.
Из недостатков: ощущается дешевле ранее упомянутых аппаратур, стики как у танго 2. Формфактор кирпичика на любителя.

<p class="image-container">
  <img src="/assets/img/mambo.webp" height="400" alt="Аппаратура TBS Mambo" title="Аппаратура TBS Mambo">
</p>

**[Jumper T-Pro](https://www.jumper-rc.com/products/transmitters/t-pro/), [Jumper T-Lite](https://www.jumper-rc.com/products/transmitters/t-lite/), [Radiomaster Zorro](https://www.radiomasterrc.com/products/zorro-radio-controller?_pos=1&_sid=49612d66c&_ss=r)** - аппаратуры близкие по формфактору к танго 2 со встроенным ЕЛРС. Да, **но..**

Цены 50-100$, некий компромисс, когда хочется компактности, есть версии со встроенным модулем ELRS и мультимодулем, не путать! У всех претендентов есть заметные минусы, рекомендуется глянуть обзоры перед покупкой, если ваш выбор пал на какую-то из них.

Главный недостаток Zorro - аккумуляторы 18350 (нестандартный труднодоступный вариант Li-Ion аккумуляторов). По наблюдениям и личному опыту с оригинальными акб от radiomaster при первых циклах после полной зарядки время работы аппаратуры 2-3 часа, спустя полгода активной эксплуатации это время сокращается до 1 часа.. будь они емкостью не 900мАч, а 3000мАч, как типовые 18650, то про зарядку приходилось бы вспоминать еще реже и время жизни было бы более продолжительным. По габаритам зорро как Radiomaster TX12, то есть несмотря на ее джойстик-стайл, экономии места в рюкзаке особо нет. Ничто не мешает иметь запасной комплект акб или подключать дополнительно внешний, но поверьте, это все же доставляет дополнительный дискомфорт.

Аппаратуры Jumper T-Pro и Jumper T-Lite имеют одну главную проблему - они от джамперов. Эта фирма из раза в раз делает кучу проблем на ровном месте. они первые выпустили аппаратуру Т16, но она была собрана на шлейфах, которые быстро ломались. Они первые сделали на первый взгляд полноценную и очень компактную аппаратуру(т-лайт), но месяц-другой, и у нее выскакивают болячки - то не включается, то что-то не работает, но что самое веселое - есть решения этих проблем от производителя на форумах, и выглядят они как "удалите этот конденсатор с платы", да-да, я бы тоже не поверила, если бы не столкнулась лично.. Что же до т-про, которая будто бы идеальная замена танго2 - у нее начинают уплывать значения стиков при повышении мощности передатчика. И самое нелепое в данной ситуации, что производитель, зная эту проблему, выпустил т-про в2, но ничего с ней не сделал.. Но так или иначе, данные аппаратуры не совсем плохи, и есть немалое количество пилотов, которое летает на них, закрывая глаза на болячки. Эти аппаратуры легко поддаются модификациям: замена антенны, стиков (на примере t-lite https://youtu.be/wslSmuW3DDI). Это позволяет кастомизировать аппу и улучшить некоторые ее детали. В качестве первой аппаратуры не хотелось бы рекомендовать их, но выбор все равно за вами.

<p class="image-container">
  <img src="/assets/img/t-pro.webp" height="300" alt="Аппаратура Jumper T-Pro" title="Аппаратура Jumper T-Pro">
  <img src="/assets/img/t-lite.webp" height="300" alt="Аппаратура Jumper T-Lite" title="Аппаратура Jumper T-Lite">
  <img src="/assets/img/zorro.webp" height="300" alt="Аппаратура RadioMaster ZORRO" title="Аппаратура RadioMaster ZORRO">
</p>

**[Jumper T-Pro](https://www.jumper-rc.com/t20-p0117.html)** - сплющенный боксер, и пока еще диковинный зверь

Цены от 110$. Есть версии с мультимодулем, ELRS на 2.4ГГц и ELRS 900МГЦ, не путайте! Стоит отметить, что стики также на выбор - на датчике Холла и резистивные, и в данном случае версия с резистивными стиками дороже. Кажется, джамперы "пофиксили" проблему уплывания значений стиков путем замены стиков, но это не точно;) Нужное количество свитчей, полноразмерные стики, относительно компактный вариант. Как покажет себя на практике - узнаем позже, народ постепенно приобретает и делится своими впечатлениями.

<p class="image-container">
  <img src="/assets/img/t20.webp" height="400" alt="Аппаратура Jumper T20" title="Аппаратура Jumper T20">
</p>

## Необходимые аксессуары

- Аккумулятор - если в аппаратуре нет встроенной батареи, то необходимо обзавестись подходящей по размеру в аппаратуру. Как правило используются сборки 2S или две ячейки Li-Ion 18650 в переходнике под 2S.
  > Отдельно прикрепляем ссылку на [статью про аккумуляторы для дронов](https://propwashservice.ru/intro/power.html)

<p class="image-container">
  <img src="/assets/img/lipoTX.webp" height="200" alt="Аккумуляторная батарея, совместимая с RadioMaster TX16S" title="Аккумуляторная батарея, совместимая с RadioMaster TX16S">
</p>

- Ремешок для шеи - держать аппаратуру в руках на весу в течении пары часов может быть ещё тем испытанием. Рекомендуется, чтобы у ремешка был Fastex (пластиковый карабин посередине) для случаев, когда необходимо положить аппаратуру, не снимая сам ремешок через голову, на которой наверняка FPV очки.

<p class="image-container">
  <img src="/assets/img/neck.webp" height="200" alt="Ремешок для шеи" title="Ремешок для шеи">
</p>

## Настройка аппаратуры

Подробная документация по EdgeTX:
https://edgetx.gitbook.io/edgetx-user-manual/b-and-w-radios

Видео со стартовой настройкой аппаратуры на базе EdgeTX:
https://www.youtube.com/watch?v=wU67j2G5Ibg
