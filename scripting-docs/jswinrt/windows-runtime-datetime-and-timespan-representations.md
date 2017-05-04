---
title: "Представления объектов DateTime и TimeSpan в среде выполнения Windows | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DateTime [JavaScript]"
  - "JavaScript, значения даты и времени в среде выполнения Windows"
  - "TimeSpan [JavaScript]"
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Представления объектов DateTime и TimeSpan в среде выполнения Windows
Представление дат и времени в JavaScript и в среде выполнения Windows различается.  Структура [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) среды выполнения Windows представлена в JavaScript в виде [Date](../javascript/reference/date-object-javascript.md) с резервным хранилищем, сравнивающим данные `DateTime` \(а также с диапазоном и точностью, отличающимися от JavaScript `Date`\).  Если изменить этот настраиваемый объект `Date`, он становится стандартным `Date` JavaScript и теряет точность.  Значения `Date` JavaScript можно передавать в `DateTime` среды выполнения Windows, где выполняется проверка их диапазона, что может привести к исключениям маршалинга.  
  
 Структура [TimeSpan](http://msdn.microsoft.com/ru-ru/c5defb66-819c-4796-85b5-07ed249a5d86) среды выполнения Windows преобразуется в миллисекунды и возвращается в виде числа JavaScript.  
  
## См. также  
 [Использование среды выполнения Windows в JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)