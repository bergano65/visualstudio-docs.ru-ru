---
title: "Внешний элемент | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Extern"
helpviewer_keywords: 
  - "Элементы схемы VSCT XML, Extern"
  - "Элемент extern (VSCT XML-схемы)"
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Внешний элемент
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Внешний элемент ссылается на файлы внешних заголовков \(.h\) для объединения файла .vsct во время компиляции. Файлы для слияния должны быть на пути включения для компилятора VSCT или ссылаться на [Включить элемент](../extensibility/include-element.md). Файлы могут быть другие vsct\-файлы или файлы заголовка C\+\+.  
  
 Определения в файлах заголовков, должны быть в формате «\#define \[символ\] \[значение\]» значение может быть другой символ, если оно определено ранее. Определения можно использовать в условных выражениях элементов команды. Любой символ, фактически не используется, будут отменены.  
  
 CommandTable Element  
Extern Element  
  
## Синтаксис  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|href|Обязательный. Путь к файлу заголовка:<br /><br /> href\="stdidcmd.h»|  
|Условие|Необязательный. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|язык|Необязательный. Язык по умолчанию для всех [\< строки \>](../extensibility/strings-element.md) элементы в таблице команд:<br /><br /> Language \= "en\-us»|  
  
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
<?xml version="1.0" encoding="utf-8"?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10- 18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema"> <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/> … <Commands package="guidMyPackage"> </CommandTable>  
```  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)