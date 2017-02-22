---
title: "IDebugProcessSecurity::GetUserName | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::GetUserName"
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает имя пользователя от поставщика порта.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```c#  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### Параметры  
 `pbstrUserName`  
 \[out\] строка, содержащая a имя пользователя.  
  
## Возвращаемое значение  
 Если метод завершается успешно, возвращается `S_OK`.  В противном случае функция возвращает код ошибки.  
  
## Заметки  
 `GetUserName` возвращает имя пользователя, которое отображается в  **Имя пользователя** столбец   **Присоединение к процессу** диалоговое окно.  Просмотр **Присоединение к процессу** откроется диалоговое окно, нажмите кнопку  **Присоединение к процессу** на  **Сервис** в меню  [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки \(ide\).  
  
## См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)