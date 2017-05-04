---
title: "Интерфейс IDebugFormatter | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugFormatter — интерфейс"
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugFormatter
Разрешает язык или интегрированная среда разработки настраивать преобразование между РАЗНЫМИ значениями и типами и строками VARTYPE.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugFormatter` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Возвращает строку, представляющую заданную ДРУГОЕ значение.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Возвращает ВАРИАНТ, содержащий заданную строку.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Возвращает строку, которая представляет заданное значение VARTYPE.|