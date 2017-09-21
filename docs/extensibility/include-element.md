---
title: "Включить элемент | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Include"
helpviewer_keywords: 
  - "Включить элемент (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, Include"
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Включить элемент
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент Include указывает файл, который можно найти на указанном экземпляре включить путь для вставки в текущий файл.  Все символы и типы, определенные станут частью скомпилированный результат.  
  
## Синтаксис  
  
```c#  
<Include href="stdidcmd.h" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|href|Обязательный. Путь к файлу заголовка:<br /><br /> href\="stdidcmd.h»|  
|Условие|Необязательный. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|Отсутствует.|Отсутствует.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды — то есть элементы меню, меню, панелей инструментов и поля со списком, который VSPackage предоставляет интегрированную среду разработки.|  
  
## Пример  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)