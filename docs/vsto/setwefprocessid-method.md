---
title: "Метод SetWefProcessId"
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
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Метод SetWefProcessId
  Предоставляет идентификатор процесса, выполняемого содержимое .NET Framework расширений Интернета \(WEF\).  
  
## Синтаксис  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### Параметры  
  
|Параметр|Описание|  
|--------------|--------------|  
|*dwProcessId*|Идентификатор процесса, который будет использоваться для выполнения содержимое WEF.|  
  
## Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли метод завершил работу.  
  
## Заметки  
 Этот метод должен вызываться после завершения процесса содержимого WEF создается, но перед тем, как любое содержимое WEF выполняется.  
  
 Если требуется интегрированную среду разработки вложить отладчик к процессу содержимого WEF, среда должна выполнить эту операцию в пользовательской реализации этого метода.  
  
  