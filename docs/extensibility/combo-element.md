---
title: Комбо Элемент Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739820"
---
# <a name="combo-element"></a>Комбо элемент
Определяет команды, которые отображаются в комбо-коробке. Есть четыре вида комбо-коробок, следующим образом: DropDownCombo, DynamicCombo, IndexCombo и MRUCombo.

## <a name="syntax"></a>Синтаксис

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный элемент. GUID идентификатора команды GUID/ID.|
|идентификатор|Обязательный элемент. Идентификатор идентификатора идентификатора команды GUID/ID.|
|по умолчаниюШирина|Обязательный элемент. Цель, который определяет ширину пикселей для комбо-коробки.|
|idCommandList|Обязательный элемент. Идентификатор, отправляемый в активную командную цель для получения списка элементов, которые будут отображаться в комбо-поле. Идентификатор будет находиться в той же области GUID, что и элемент управления.|
|priority|Необязательный параметр. Числовое значение, которое определяет приоритет.|
|type|Необязательный параметр. Перечисленное значение, опоглавиваещее тип кнопки.<br /><br /> Если не дано, использует кнопку.<br /><br /> DropDownCombo<br /> VSPackage отвечает за заполнение содержимого для этого комбо-коробки. Пользователь не может ввести что-либо в текстовом поле этого выпадения.<br /><br /> ДинамическийКомбо<br /> VSPackage отвечает за заполнение содержимого этого комбо-коробки. Пользователь может отсеить этот комбо, а также выбрать элементы в нем.<br /><br /> ИндексКомбо<br /> Так же, как DynamicCombo, за исключением того, что он поднимает индекс элемента, а не его текст.<br /><br /> MRUCombo<br /> Заполнен интегрированной средой разработки (IDE) от имени VSPackage.  Пользователь может отослать в этом комбо-поле. IDE помнит до последних 16 записей на комбо-бокс.<br /><br /> Когда пользователь выбирает что-то в комбо-коробке или вводит что-то новое, IDE уведомляет соответствующий VSPackage.|
|Условие|Необязательный параметр. Посмотреть [условные атрибуты.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Parent|Необязательный параметр. Родительский элемент кнопки.|
|CommandFlag|Обязательный элемент. Посмотреть [элемент флага команды](../extensibility/command-flag-element.md). Действительные значения CommandFlag для кнопки следующие.<br /><br /> - ДелоЧувствательная<br /><br /> - CommandWellOnly<br /><br /> - Инвалиды по умолчанию<br /><br /> - По умолчаниюневидимый<br /><br /> - Динамическаявидимость<br /><br /> - FilterKeys<br /><br /> - IconAndText<br /><br /> - NoAutoComplete<br /><br /> - NoButtonCustomize<br /><br /> - Нет Настройка<br /><br /> - NoKeyCustomize<br /><br /> - РастяжениеГоризонтально|
|Строки|Обязательный элемент. Посмотреть [элемент строки](../extensibility/strings-element.md). Элемент «ребенок ButtonText» должен быть определен.|
|Заметка|Дополнительный комментарий.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент команд](../extensibility/commands-element.md)|Представляет коллекцию команд на панели инструментов VSPackage.|

## <a name="example"></a>Пример

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>См. также
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
