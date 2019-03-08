## Расположение шагов.

$dir = \bitrix\modules\\*new module*\install\step

Каждый шаг должен иметь название Step и значение в порядке возрастания.
step1.php, step2.php, step3.php и т.д. Каждый Step может иметь свой script.js. название должно быть аналогичным. step2.js
$dir\body - Хранятся шаблоны 1) Основных шагов 2) Финиша 3) Удаления модуля. 
Конец установки в файле finish.php
spte,finish должны вернуть return array []; Для быстроты работы нужно использовать класс CStepв

## Логика работы CStep UI.
Для быстрого формирования шагов используется класс CStep.

Cstep может строиться с Admin Tab Control, так и без него.

### BoxTitle
Задает заголовок шагу вне таба. 
`CStep::BoxTitle(string $title),`

### BoxInstruction
Создает блок с информацией. можно использовать к примеру для правил установок или настроек.
`CStep::BoxInstruction(string $instruction),`

### BoxSmall

### inputHidden
`CStep::inputHidden(string||false,string $name_code,string $value)`

### inputText
`CStep::inputText(string||false, string $name_code,string $value,string $name, array $attr||false,array $data||false)`

### inputCheckbox
`CStep::inputText(string||false, string $name_code,string $value,string $name, array $attr||false,array $data||false)`

### selected
`CStep::selected(string||false, string $name_code,string $option,string $name, string $selected||false, array $attr||false,array $data||false)`

### Custom
`CStep::Custom(string $name,function callable $f)`

### CHtml
`CStep::CHtml(function callable $f)`

### groupTab
`CStep::groupTab(string $code,string $title,array $input)`

Пример использования: 

`CStep::groupTab('settings.option','Основные настройки', [
        CStep::inputText('USER','NAME','Четкая','Твоя компания:',['required']),
        CStep::selected('USER','GROUP',['Да','Нет','Что??'],'Да?:',2,['required'],['code'=>'name ']),
]),`
