---
title: "IActiveScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptError — интерфейс"
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError
Объект, реализующий этот интерфейс передается методу [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md), когда обработчик скриптов сталкивается с необработанной ошибкой.  Затем основное приложение вызывает методы в этом объекте для получения сведений об ошибке, которая возникла.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Извлекает сведения об ошибке.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Извлекает местоположение в исходном коде, где произошла ошибка.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Извлекает линию в исходном файле, где произошла ошибка.|  
  
## См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)