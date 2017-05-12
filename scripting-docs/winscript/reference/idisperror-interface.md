---
title: "Интерфейс IDispError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispError — интерфейс"
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDispError
Предоставляет детализировал контекстные сведения об ошибке.  
  
> [!NOTE]
>  Этот интерфейс не реализован.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDispError` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Извлекает указанный тип сведений об ошибке.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Извлекает следующий объект `IDispError`.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Извлекает код ошибки из объекта `IDispError`.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Возвращает идентификатор progid зависящим от языка для класса или приложения, подняли ошибку.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Возвращает путь к файлу Справки и контекстного идентификатора разделы с описанием ошибки, если возможно.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Возвращает текстовое описание ошибки.|