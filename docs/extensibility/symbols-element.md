---
title: "Элемент символы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элемент символы (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, символы"
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Элемент символы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет идентификаторы GUID и идентификаторов, используемых другими элементами VSCT. Для неуправляемого кода эти сведения обычно берутся из файлов заголовков, которые указываются с помощью [Внешний элемент](../extensibility/extern-element.md). Управляемый код использует дочерние элементы элемента символы, чтобы определить сведения об этом.  
  
 При создании файла .vsct из существующего файла .cto символы будут создаваться как дочерние элементы элемента символы. Дополнительные сведения см. в разделе [Практическое руководство. Создание файла VSCT на основе существующего файла CTO](../Topic/How%20to:%20Create%20a%20.Vsct%20File%20from%20an%20Existing%20.Cto%20File.md).  
  
 Элемент символы не следует путать с [Определение элемента](../extensibility/define-element.md), определяющего пары имя значение для использования препроцессором.  
  
## Синтаксис  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|Нет||  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|GuidSymbol|Определяет символ идентификатора GUID. GuidSymbol имеет два обязательных атрибута: имя и значение. Имя — имя символа, а значение является значением идентификатора GUID, как строка.<br /><br /> Например: \< GuidSymbol имя \= значение «guidVsPackage1Pkg» \= "{c5f54698\-101a\-4846\-84d3\-dc748f9cd848}" \/ \>|  
|IDSymbol|Определяет символ. IDSymbol имеет два обязательных атрибута: имя и значение. Имя — имя символа, а значение является значением символа в виде строки.<br /><br /> Например: \< IDSymbol имя \= значение «MyMenuGroup» \= «0x1020»\-\>|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Корневой элемент файла .vsct.|  
  
## Пример  
  
```  
<Symbols> <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" /> <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="cmdidMyCommand" value="0x0100" /> <IDSymbol name="cmdidMyTool" value="0x0101" /> </GuidSymbol> </Symbols>  
```  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)