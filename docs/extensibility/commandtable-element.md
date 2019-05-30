---
title: Элемент CommandTable | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9bb10232c725eb2f538df73f6a7ca98e534a4c14
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341803"
---
# <a name="commandtable-element"></a>Элемент CommandTable
CommandTable является корневым элементом *.vsct* файла. Это файл, который определяет фактическую структуру и тип команды, которые VSPackage предоставляет интегрированную среду разработки. Команды могут включать элементы меню, меню, панелей инструментов и поля со списком. Дополнительные сведения см. в разделе [Visual Studio командные table (.vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

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
| xmlns | Обязательный. Пространства имен XML:<br /><br /> xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| язык | Необязательный параметр. Атрибут языка может использоваться для указания языка по умолчанию всех \<строки > элементы в таблице команд.  Если язык не указан, будет использоваться язык текущего процесса:<br /><br /> language="en-us" |

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент extern](../extensibility/extern-element.md)|Необязательный параметр. Содержит директивы препроцессора для компилятора.|
|[Включить элемент](../extensibility/include-element.md)|Необязательный параметр. Содержит пути к любым файлам, чтобы включить в компиляцию.|
|[Определение элемента](../extensibility/define-element.md)|Необязательный параметр. Определяет символ, ее имя и значение.|
|[Элемент Commands](../extensibility/commands-element.md)|Необязательный параметр. Родительский элемент, определение всех команд для VSPackage, который содержит все остальные элементы.|
|[Элемент CommandPlacements](../extensibility/commandplacements-element.md)|Необязательный параметр. Определяет, где на панели команд, команды должны располагаться.|
|[Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Необязательный параметр. Определяет статические видимость команды и панели инструментов.|
|[Элемент KeyBindings](../extensibility/keybindings-element.md)|Необязательный параметр. Задает сочетания клавиш, если таковые имеются, для команд.|
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Необязательный параметр. Разрешает VSPackage при необходимости реализовать свою собственную версию функции, изначально поддерживаемые других пакетов VSPackage.|
|[Элемент Symbols](https://www.microsoft.com/download/details.aspx?id=55984)|Необязательный параметр. Содержит все данные символов--идентификаторы GUID, идентификаторы и т.д. — для компилятора.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|Нет||

## <a name="see-also"></a>См. также
- [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)