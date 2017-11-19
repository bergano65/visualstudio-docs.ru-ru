---
title: "Элемент CommandTable | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4f1a906f545dcdbaefca7f5a38824a1f3259c97
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="commandtable-element"></a>Элемент CommandTable
CommandTable является корневым элементом файла vsct. Это файл, определяющий фактическое размещение и типы команд, которые VSPackage предоставляет интегрированную среду разработки. Команды могут включать элементы меню, меню, панелей инструментов и поля со списком. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|xmlns|Обязательный. Пространства имен XML.<br /><br /> xmlns = «http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable»<br /><br /> xmlns:xs = «http://www.w3.org/2001/XMLSchema»|  
|язык|Необязательно. Атрибут language может использоваться для указания языка по умолчанию всех \<строки > элементов в таблице команд.  Если язык не указан, будет использован язык текущего процесса:<br /><br /> Language = "en-us»|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Extern](../extensibility/extern-element.md)|Необязательно. Содержит директивы препроцессора для компилятора.|  
|[Элемент Include](../extensibility/include-element.md)|Необязательно. Содержит пути все файлы, включаемые в компиляцию.|  
|[Элемент Define](../extensibility/define-element.md)|Необязательно. Определяет символ, по его имени и значения.|  
|[Элемент Commands](../extensibility/commands-element.md)|Необязательно. Родительский элемент, определение всех команд для VSPackage, содержащий все остальные элементы.|  
|[Элемент CommandPlacements](../extensibility/commandplacements-element.md)|Необязательно. Определяет, где на панели команд команды должны быть помещены.|  
|[Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Необязательно. Определяет видимость статических команды и панели инструментов.|  
|[Элемент KeyBindings](../extensibility/keybindings-element.md)|Необязательно. Задает сочетание клавиш, если таковые имеются, для команд.|  
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Необязательно. Позволяет пакету VSPackage при необходимости реализовать собственную версию функции, изначально поддерживаемые других пакетов VSPackage.|  
|[Элемент Symbols](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Необязательно. Содержит все данные символов--идентификаторы GUID, идентификаторы и т. д. — для компилятора.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Нет||  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)