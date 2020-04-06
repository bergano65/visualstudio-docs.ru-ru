---
title: Элемент командного размещения Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandPlacements element (VSCT XML schema)
- VSCT XML schema elements, CommandPlacements
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf9f23b5e860b895baa4c2a7a783f2ee15fcc77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739742"
---
# <a name="commandplacement-element"></a>Элемент командного размещения
Элемент CommandPlacement позволяет включать кнопки, группы и меню в более чем одну группу или меню. Используя элемент CommandPlacement, вам не придется полностью переопределять эти элементы, чтобы изменить внешний вид пользовательского интерфейса.

 Для получения дополнительной [информации см.](../extensibility/creating-reusable-groups-of-buttons.md)

## <a name="syntax"></a>Синтаксис

```
<CommandPlacement guid="guidMyCommandSet" id="MyCommand" priority="0x001" >
  <Parent>... </Parent>
</CommandPlacement>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный элемент. Руководство набора команд, как определено в [элементе Символов.](../extensibility/symbols-element.md)|
|идентификатор|Обязательный элемент. Идентификатор меню, группы или команды, которые `Symbols Element`должны быть размещены, как определено в .|
|priority|Обязательный элемент. Определяет визуальное положение элемента в его родительском элементе.|
|Условие|Необязательный параметр. Смотрите [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Parent|Обязательный элемент. Меню или группа, в размещении которого размещается товар.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент командных мест](../extensibility/commandplacements-element.md)|Определяет группы командных мест и элементов командного заклада.|

## <a name="example"></a>Пример

```
<CommandPlacements>
  <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions"
    priority="0x0300">
    <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/>
  </CommandPlacement>
</CommandPlacements>
```

## <a name="see-also"></a>См. также
- [Элемент командных мест](../extensibility/commandplacements-element.md)
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
