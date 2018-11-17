---
title: Элемент CommandTable | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1adc3e8f8c7894cfb3a55617ce594f52a60f2498
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817377"
---
# <a name="commandtable-element"></a>Элемент CommandTable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable является корневым элементом файла .vsct. Это файл, который определяет фактическую структуру и тип команды, которые VSPackage предоставляет интегрированную среду разработки. Команды могут включать элементы меню, меню, панелей инструментов и поля со списком. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
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
  
| Атрибут |                                                                                                                   Описание:                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Обязательно. Пространства имен XML:<br /><br /> xmlns =»<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:xs =»<http://www.w3.org/2001/XMLSchema>"                                   |
| язык  | Необязательный. Атрибут языка может использоваться для указания языка по умолчанию всех \<строки > элементы в таблице команд.  Если язык не указан, будет использоваться язык текущего процесса:<br /><br /> Language = "en-us» |
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент Extern](../extensibility/extern-element.md)|Необязательный. Содержит директивы препроцессора для компилятора.|  
|[Элемент Include](../extensibility/include-element.md)|Необязательный. Содержит пути к любым файлам, чтобы включить в компиляцию.|  
|[Элемент Define](../extensibility/define-element.md)|Необязательный. Определяет символ, ее имя и значение.|  
|[Элемент Commands](../extensibility/commands-element.md)|Необязательный. Родительский элемент, определение всех команд для VSPackage, который содержит все остальные элементы.|  
|[Элемент CommandPlacements](../extensibility/commandplacements-element.md)|Необязательный. Определяет, где на панели команд, команды должны располагаться.|  
|[Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Необязательный. Определяет статические видимость команды и панели инструментов.|  
|[Элемент KeyBindings](../extensibility/keybindings-element.md)|Необязательный. Задает сочетания клавиш, если таковые имеются, для команд.|  
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Необязательный. Разрешает VSPackage при необходимости реализовать свою собственную версию функции, изначально поддерживаемые других пакетов VSPackage.|  
|[Элемент Symbols](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Необязательный. Содержит все данные символов--идентификаторы GUID, идентификаторы и т.д. — для компилятора.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|Нет||  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

