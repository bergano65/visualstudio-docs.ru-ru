---
title: "Метод GetAutoInsertExtensions | Microsoft Docs"
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
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Метод GetAutoInsertExtensions
  Возвращает сведения о приложениях для office, автоматически вставляются во время отладки.  
  
 Этот метод зарезервирован для использования в будущем.  
  
## Синтаксис  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### Параметры  
  
|Параметр|Описание|  
|--------------|--------------|  
|*psaExtensionNames*|Имена для расширения приложений office.|  
  
## Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли метод завершил работу.  
  
## Заметки  
 Каждое приложение для office для вставки возвращается как имя расширения приложений office, соответствующее значению в разделе HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\WEF\\Developer.  Основное приложение должно искать эти значения в реестре и затем автоматически вставлять расширения.  
  
  