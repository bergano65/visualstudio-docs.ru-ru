---
title: Элемент CommandTable Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739645"
---
# <a name="commandtable-element"></a>Элемент CommandTable
CommandTable — это корневой элемент файла *.vsct.* Это файл, который определяет фактическое расположение и тип команд, которые VSPackage предоставляет IDE. Команды могут включать в себя пункты меню, меню, панели инструментов и комбо-коробки. Для получения дополнительной информации смотрите [файлы командной таблицы Visual Studio (.vsct).](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

## <a name="syntax"></a>Синтаксис

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

| Атрибут | Описание |
|-----------| - |
| xmlns | Обязательный элемент. XML пространства имен:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs"<http://www.w3.org/2001/XMLSchema>" |
| Язык | Необязательный параметр. Атрибут языка может использоваться для указания \<языка по умолчанию всех строк> элементов в таблице команд.  Если язык не указан, язык текущего процесса будет использоваться:<br /><br /> язык "ан-нас" |

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Экстерн](../extensibility/extern-element.md)|Необязательный параметр. Содержит предпроцессорные директивы для компилятора.|
|[Включить элемент](../extensibility/include-element.md)|Необязательный параметр. Содержит пути к любым файлам для включения в компилю.|
|[Определить элемент](../extensibility/define-element.md)|Необязательный параметр. Определяет символ, учитывая его название и ценность.|
|[Элемент команд](../extensibility/commands-element.md)|Необязательный параметр. Родительский элемент, определяющий все команды для VSPackage, содержащий все остальные элементы.|
|[Элемент командных мест](../extensibility/commandplacements-element.md)|Необязательный параметр. Определяет, где на панели команд должны быть размещены команды.|
|[Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Необязательный параметр. Определяет статическую видимость команд и панелей инструментов.|
|[Элемент KeyBindings](../extensibility/keybindings-element.md)|Необязательный параметр. Определяет комбинации ключей ярлыка, если таковые имеется, для команд.|
|[Элемент подержанных команд](../extensibility/usedcommands-element.md)|Необязательный параметр. Позволяет VSPackage дополнительно реализовать свою собственную версию функциональности, первоначально поддерживаемой другими VSPackages.|
|[Элемент символов](https://www.microsoft.com/download/details.aspx?id=55984)|Необязательный параметр. Содержит любые данные символов - GUID, идентионные данные и т.д. - для компилятора.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|None||

## <a name="see-also"></a>См. также
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
