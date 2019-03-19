# oxy-gost

Стили ГОСТ ЕСПД для OxygenXML и проект для тестирования стилей.  
**Версия OxygenXML**: OxygenXML 20.1, OxygenXML 21.1  
**Язык**: Русский, Russian

В папке `common/gosthtml` - сами CSS стили. В папке `/project` - тестовый проект .xpr для загрузки в OxygenXML. В проекте сохранен сценарий трансформации с настройками.

## Использование

Набор стилей включает нсколько файлов CSS, сгруппированных по элементам:
- `/common/gosthtml/ge-cover.css` - оформление титула, надписи на титуле; 
- `/common/gosthtml/ge-figures.css` - оформление рисунков; 
- `/common/gosthtml/ge-lists.css` - оформление списокв; 
- `/common/gosthtml/ge-numbering.css` - нумерация заголовков; 
- `/common/gosthtml/ge-page-setup.css` - поля, шрифты; 
- `/common/gosthtml/ge-ru.css` - русификация надписей; 
- `/common/gosthtml/ge-tables.css` - таблицы.

В проекте-примере стили подключены в файле `/project/styles.css`. Стили можно подключить все сразу, или только нужные (например, если не нужны строгие списки по ГОСТ).

Настройка OxygenXML для работы со стилями: 
- чтобы рисунки и таблицы назывались *«Рисунок 1 - …»*, *«Таблица 1 - …»*,  а CONTENT назывался *«Содержание»*, нужно подключить CSS с локализованными строками, например, в этом проекте подключен файл `ge-ru.css`, в котором эти названия локализованы (вы можете использовать свой); 
- чтобы ссылки на рисунки и таблицы были просто цифрой (без «Рисунок »), нужно в файле `C:\Program Files\Oxygen XML Editor 21\frameworks\dita\DITA-OT3.x\plugins\org.dita.pdf2\cfg\common\vars\ru.xml` поправить строки `<variable id="Figure Number">` и `<variable id="Table Number">` (уберите надписи *Рисунок* и *Таблица* и сохраните файл).

Для вывода pdf используется сценарий на основе стандартного *DITA Map PDF - based on HTML5 & CSS*. Сценарий трансформации сохранен в этом проекте. Параметры указаны в таблице:

| Параметр                        | Значение        |
| ------------------------------- | --------------- |
| args.css                        | ${pd}/style.css |
| args.figurelink.style           | NUMBER          |
| args.input                      | ${cf}           |
| args.tablelink.style            | NUMBER          |
| default.language                | ru              |
| figure.title.placement          | bottom          |
| fix.external.refx.com.oxygenxml | true            |
| generate.copy.outer             | 3               |

## Пример

В собранном документе и в файлах исходника проекта.  
[Пример собранного документа в PDF](https://github.com/annjulyleon/oxy-gost/blob/master/project/out/pdf-css-html5/rd-13.pdf).
