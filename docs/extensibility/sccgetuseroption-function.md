---
title: "Функция SccGetUserOption | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGetUserOption"
helpviewer_keywords: 
  - "Функция SccGetUserOption"
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Функция SccGetUserOption
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Эта функция извлекает различные параметры для конкретного пользователя.  
  
## Синтаксис  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### Параметры  
 pContext  
 \[in\] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 nOption  
 \[in\] Возможность получить \(см. примечания для возможных вариантов\).  
  
 lpVal  
 \[out\] Значение, связанное с параметром.  
  
## Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|--------------|--------------|  
|SCC\_OK|Параметр был успешно извлечен.|  
|SCC\_E\_OPNOTSUPPORTED|Параметр не поддерживается.|  
|SCC\_E\_NONSPECIFICERROR|Произошла неизвестная ошибка.|  
  
## Заметки  
 При помощи этой команды поддерживаются следующие параметры:  
  
|Параметр User|Описание|  
|-------------------|--------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Определяет, является ли пользователь хочет извлечь локальную версию файлов.`lpVal` назначается `SCC_USEROPT_COLV_YES` \(пользователь хочет извлечь локальных файлов\) или `SCC_USEROPT_COLV_NO`.|  
  
## См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [Коды ошибок](../extensibility/error-codes.md)