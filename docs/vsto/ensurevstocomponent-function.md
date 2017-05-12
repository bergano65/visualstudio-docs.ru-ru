---
title: "Функция EnsureVSTOComponent"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: e101fcd5-37a2-4b8c-b9ac-a84624298736
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Функция EnsureVSTOComponent
  Этот API office поддерживает инфраструктуру и не предназначено для использования непосредственно из программного кода.  
  
## Синтаксис  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### Параметры  
  
|Параметр|Описание|  
|--------------|--------------|  
|*pProject*|Не используйте.|  
  
## Возвращаемое значение  
 Если функция завершается успешно, возвращается **S\_ОК**.  Если функция завершается неудачей, то она возвращает код ошибки.  
  
  