---
title: "Интерфейс IPerPropertyBrowsing2 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2 — интерфейс"
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Интерфейс IPerPropertyBrowsing2
Осуществляет доступ к сведениям на страницах свойств предлагаемых объектом.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|`GetDisplayString`|Возвращает текстовую строку, описывающую указанное свойство.|  
|`MapPropertyToPage`|Возвращает идентификатор CLSID страницы свойств, которая позволяет управлять указанного свойства.|  
|`GetPredefinedStrings`|Возвращает подсчитанный массив строк \(для указателей\)`LPOLESTR` какие описания допустимых значений, указанное свойство может принимать.|  
|`SetPredefinedValue`|Присваивает значение свойства к значению, указанному `dwCookie.` токеном предопределенному|  
  
## Требования  
 Заголовок: dbgprop.h