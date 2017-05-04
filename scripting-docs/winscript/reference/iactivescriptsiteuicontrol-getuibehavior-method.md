---
title: "Метод IActiveScriptSiteUIControl::GetUIBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Метод IActiveScriptSiteUIControl::GetUIBehavior
Возвращает [Перечисление SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md), представляющий способ управления пользовательского интерфейса, который должен быть обращано.  
  
## Синтаксис  
  
```  
HRESULT GetUIBehavior(   
    [in] SCRIPTUICITEM UicItem,   
    [out] SCRIPTUICHANDLING * pUicHandling   
);  
  
```  
  
#### Параметры  
 `UicItem`  
 Тип элемента управления.  
  
 `pUicHandling`  
 Способ элемент управления должен быть обращан.