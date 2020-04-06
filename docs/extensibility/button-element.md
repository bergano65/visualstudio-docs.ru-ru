---
title: Элемент кнопки Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739938"
---
# <a name="button-element"></a>Элемент кнопки
Определяет элемент, с которым пользователь может взаимодействовать. Кнопки могут быть разных видов: кнопки, MenuButton и SplitDropDown.

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
|guid|Обязательный элемент. GUID идентификатора команды GUID/ID.|
|идентификатор|Обязательный элемент. Идентификатор идентификатора идентификатора команды GUID/ID.|
|priority|Необязательный параметр. Числовое значение, которое определяет приоритет.|
|type|Необязательный параметр. Перечисленное значение, которое определяет вид кнопки.<br /><br /> Если не дано, использует кнопку.<br /><br /> Кнопка<br /> Стандартная команда, которая отображается на панели инструментов (обычно в виде знаковой кнопки), меню и контекстных меню.<br /><br /> МенюБаттл<br /> Элемент меню, который не выполняет команду, но производит другое меню.<br /><br /> SplitDropDown<br /> Элементы управления, такие как кнопки «Отменить» и «Редо» на стандартной панели инструментов в Microsoft Word.|
|Условие|Необязательный параметр. Посмотреть [условные атрибуты.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Родительский элемент](../extensibility/parent-element.md)|Необязательный параметр. Родительский элемент кнопки.|
|[Элемент значка](../extensibility/icon-element.md)|Необязательный параметр. Значок, связанный с кнопкой.|
|[Элемент флага командования](../extensibility/command-flag-element.md)|Обязательный элемент. Действительные значения CommandFlag для кнопки следующие.<br /><br /> - РазрешитьПарамс<br /><br /> - CommandWellOnly<br /><br /> - Инвалиды по умолчанию<br /><br /> - По умолчаниюневидимый<br /><br /> - DontCache<br /><br /> - Динамичное начало<br /><br /> - Динамическаявидимость<br /><br /> - FixMenuКонтроллер<br /><br /> - IconAndText<br /><br /> - NoButtonCustomize<br /><br /> - Нет Настройка<br /><br /> - NoKeyCustomize<br /><br /> - НошовонМенуменуареер<br /><br /> - Пикт<br /><br /> - PostExec<br /><br /> - ПредложениеCmd<br /><br /> - RouteToDocs<br /><br /> - TextCascadeUseBtn<br /><br /> - TextMenuUseButton<br /><br /> - TextChanges<br /><br /> - TextChangesButton<br /><br /> - TextContextUseButton<br /><br /> - TextMenuCtrlUseМеню<br /><br /> - TextMenuUseButton<br /><br /> - TextOnly|
|[Элемент струн](../extensibility/strings-element.md)|Обязательный элемент. Элемент «ребенок [ButtonText»](../extensibility/buttontext-element.md) должен быть определен.|
|Заметка|Дополнительный комментарий.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент кнопки](../extensibility/buttons-element.md)|Элементы кнопки групп.|

## <a name="example"></a>Пример
 Следующий пример определяет кнопку в файле *.vsct.*

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
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
