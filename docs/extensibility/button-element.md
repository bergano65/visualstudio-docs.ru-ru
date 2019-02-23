---
title: Кнопки элемент | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e62436d32d85c76685c86ea0da396dacae1bf3f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694274"
---
# <a name="button-element"></a>Элемент Button
Определяет элемент, который пользователь может взаимодействовать с. Кнопки могут быть разных типов: Кнопка, MenuButton и SplitDropDown.

## <a name="syntax"></a>Синтаксис

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный. Идентификатор GUID идентификатора GUID и идентификатора команды.|
|id|Обязательный. Идентификатор GUID и идентификатора идентификатор команды.|
|priority|Необязательный параметр. Числовое значение, указывающее приоритет.|
|type|Необязательный параметр. Значение перечисления, которое указывает тип кнопки.<br /><br /> Если не указан, используется кнопка.<br /><br /> Кнопка<br /> Стандартные команды, которая отображается на панели инструментов (обычно виде преобразованного в значок кнопки), меню и контекстные меню.<br /><br /> MenuButton<br /> Пункт меню, который не выполняет команду, но дает другое меню.<br /><br /> SplitDropDown<br /> Элементы управления, например кнопки отмены и повтора на стандартной панели инструментов в Microsoft Word.|
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание:|
|-------------|-----------------|
|[Родительский элемент](../extensibility/parent-element.md)|Необязательный параметр. Родительский элемент кнопки.|
|[Элемент Icon](../extensibility/icon-element.md)|Необязательный параметр. Значок, связанный с кнопкой.|
|[Элемент commandflag](../extensibility/command-flag-element.md)|Обязательный. Ниже приведены допустимые значения CommandFlag для кнопки.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly|
|[Элемент strings](../extensibility/strings-element.md)|Обязательный. Дочерние [элемент ButtonText](../extensibility/buttontext-element.md) должен быть определен.|
|Комментарий|Дополнительный комментарий.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Buttons](../extensibility/buttons-element.md)|Группирует элементы кнопки.|

## <a name="example"></a>Пример
 В следующем примере определяется кнопки в *.vsct* файла.

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>См. также
- [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)