---
title: "Определение элемента | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элементы схемы VSCT XML, определение"
  - "Определение элемента (VSCT XML-схемы)"
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Определение элемента
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет пару символов имени и значения. Этот символ можно использовать для оценки условные атрибуты. Дополнительные сведения см. в разделе [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md). См. также [Элемент символы](../extensibility/symbols-element.md).  
  
## Синтаксис  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|имя|Обязательный. Имя символа:<br /><br /> Имя \= «Режим»|  
|значение|Обязательный. Значение символа:<br /><br /> значение \= «Standard»|  
|Условие|Необязательный. Дополнительные сведения см. в разделе [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Дочерние элементы  
 Отсутствует.  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, которые VSPackage предоставляет интегрированную среду разработки \(IDE\). Например элементы меню, меню, панелей инструментов и поля со списком.|  
  
## Пример  
  
```  
<Define name="DEMO_UI"/> <Define name="MODE" value="Standard"/>  
```  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)