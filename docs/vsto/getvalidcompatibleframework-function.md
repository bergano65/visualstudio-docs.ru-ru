---
title: "Функция GetValidCompatibleFramework"
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
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Функция GetValidCompatibleFramework
  Этот API office поддерживает инфраструктуру и не предназначено для использования непосредственно из программного кода.  
  
## Синтаксис  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### Параметры  
  
|Параметр|Описание|  
|--------------|--------------|  
|*lpwszCompatibleFrameworksXML*|Не используйте.|  
|*pbstrValidFrameworkTag*|Не используйте.|  
  
## Возвращаемое значение  
 Если функция завершается успешно, возвращается **S\_ОК**.  Если функция завершается неудачей, то она возвращает код ошибки.  
  
  