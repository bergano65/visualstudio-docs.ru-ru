---
title: "Элемент CommandTable | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4a6abf25d0e3eff335c8a6fe62affc19d8037afa
ms.lasthandoff: 02/22/2017

---
# <a name="commandtable-element"></a>Элемент CommandTable
CommandTable является корневым элементом файла .vsct. Это файл, определяющий фактическая структура и тип команд, которые VSPackage предоставляет интегрированную среду разработки. Команды могут включать элементы меню, меню, панелей инструментов и поля со списком. Дополнительные сведения см. в разделе [таблицы команд Visual Studio (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
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
|xmlns|Обязательный. Пространства имен XML:<br /><br /> xmlns = «http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable»<br /><br /> xmlns:xs = «http://www.w3.org/2001/XMLSchema»|  
|язык|Необязательный. Атрибут language может использоваться для указания языка по умолчанию для всех \<строки настроек элементы в таблице команд.  Если язык не указан, будет использован язык текущего процесса:<br /><br /> Language = "en-us»|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Внешний элемент](../extensibility/extern-element.md)|Необязательный. Содержит директивы препроцессора для компилятора.|  
|[Включить элемент](../extensibility/include-element.md)|Необязательный. Содержит пути к любым файлам, чтобы включить в процессе компиляции.|  
|[Определение элемента](../extensibility/define-element.md)|Необязательный. Определяет символ, по его имени и значения.|  
|[Элемент Commands](../extensibility/commands-element.md)|Необязательный. Родительский элемент, определение всех команд для VSPackage, содержащий все остальные элементы.|  
|[Элемент CommandPlacements](../extensibility/commandplacements-element.md)|Необязательный. Определяет, где в командной строке команды должны быть помещены.|  
|[Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Необязательный. Определяет видимость статических команды и панели инструментов.|  
|[Элемент привязки клавиш](../extensibility/keybindings-element.md)|Необязательный. Указывает сочетаний клавиш, если таковые имеются, для команд.|  
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Необязательный. Позволяет при необходимости реализовать собственную версию функции, изначально поддерживаемые другие пакеты VSPackage VSPackage.|  
|[Элемент символы](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Необязательный. Содержит все данные символов--идентификаторы GUID, идентификаторы и т.д. — для компилятора.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Нет||  
  
## <a name="see-also"></a>См. также  
 [Таблицы команд Visual Studio (. Файлы Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
