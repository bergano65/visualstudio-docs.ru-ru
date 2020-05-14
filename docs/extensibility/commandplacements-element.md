---
title: Элемент командных мест Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandPlacements
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a72b087652a654b563fd4e00bacc52290a29fe1c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739696"
---
# <a name="commandplacements-element"></a>Элемент командных мест
Элементы командных мест группируют элементы командного замыкания и другие группировки командных мест.

 Элемент CommandPlacements не является обязательным. Если команды, группы или меню не должны быть включены во вторичное место, вам не нужно включать этот раздел в файл *.vsct.*

## <a name="syntax"></a>Синтаксис

```xml
<CommandPlacements>
  <CommandPlacement>... </CommandPlacement>
  <CommandPlacement>... </CommandPlacement>
</CommandPlacements>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|Условие|Необязательный параметр. Посмотреть [условные атрибуты.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Командные места|Элементы командного пункта и другие командные группы.|
|[Элемент командного размещения](../extensibility/commandplacement-element.md)|Позволяет включать кнопки, группы и меню в более чем одну группу или меню.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды.|

## <a name="example"></a>Пример

```xml
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>См. также
- [Элемент командного размещения](../extensibility/commandplacement-element.md)
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
