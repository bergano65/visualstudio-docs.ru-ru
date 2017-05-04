---
title: "Функция GetVstoSolutionMetadata | Microsoft Docs"
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
ms.assetid: e8195838-fb9f-42b2-bb76-7ae3753f7751
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Функция GetVstoSolutionMetadata
  Этот API office поддерживает инфраструктуру и не предназначено для использования непосредственно из программного кода.  
  
## Синтаксис  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### Параметры  
  
|Параметр|Описание|  
|--------------|--------------|  
|*lpwszSolutionMetadataKey*|Не используйте.|  
|*ppSolutionInfo*|Не используйте.|  
  
## Возвращаемое значение  
 Если функция завершается успешно, возвращается **S\_ОК**.  Если функция завершается неудачей, то она возвращает код ошибки.  
  
  