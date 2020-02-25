---
title: Элемент Коммандтабле | Документация Майкрософт
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
ms.openlocfilehash: f577b52ad2a9b1fd66ed9c24fb2737621aa8554c
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557780"
---
# <a name="commandtable-element"></a>Коммандтабле, элемент
Коммандтабле — это корневой элемент *vsct* -файла. Это файл, который определяет фактический макет и тип команд, которые пакет VSPackage предоставляет интегрированной среде разработки. Команды могут включать пункты меню, меню, панели инструментов и поля со списком. Дополнительные сведения см. в разделе [файлы командных таблиц Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

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
 Следующие разделы описывают атрибуты, дочерние элементы и родительские элементы.

### <a name="attributes"></a>Атрибуты

| Атрибут | Описание |
|-----------| - |
| xmlns | Обязательное. Пространства имен XML:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns: XS = "<http://www.w3.org/2001/XMLSchema>" |
| язык | Необязательно. Атрибут Language можно использовать для указания языка по умолчанию для всех \<строк, > элементов в таблице команд.  Если язык не указан, будет использоваться язык текущего процесса:<br /><br /> Language = "en-US" |

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Внешний элемент](../extensibility/extern-element.md)|Необязательно. Содержит директивы препроцессора для компилятора.|
|[Включить элемент](../extensibility/include-element.md)|Необязательно. Содержит пути к любым файлам, которые необходимо включить в компиляцию.|
|[Определение элемента](../extensibility/define-element.md)|Необязательно. Определяет символ с учетом его имени и значения.|
|[Commands, элемент](../extensibility/commands-element.md)|Необязательно. Родительский элемент, определяющий все команды для VSPackage, которые содержат все остальные элементы.|
|[CommandPlacements, элемент](../extensibility/commandplacements-element.md)|Необязательно. Определяет, где на панели команд должны размещаться команды.|
|[Висибилитиконстраинтс, элемент](../extensibility/visibilityconstraints-element.md)|Необязательно. Определяет статическую видимость команд и панелей инструментов.|
|[Сочетания клавиш, элемент](../extensibility/keybindings-element.md)|Необязательно. Задает сочетания клавиш, если они есть, для команд.|
|[Уседкоммандс, элемент](../extensibility/usedcommands-element.md)|Необязательно. Позволяет пакету VSPackage при необходимости реализовать собственную версию функциональности, изначально поддерживаемую другими пакетами VSPackage.|
|[Элемент Symbols](https://www.microsoft.com/download/details.aspx?id=55984)|Необязательно. Содержит любые символьные данные — идентификаторы GUID, идентификаторы и т. д. для компилятора.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|Нет||

## <a name="see-also"></a>См. также:
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)