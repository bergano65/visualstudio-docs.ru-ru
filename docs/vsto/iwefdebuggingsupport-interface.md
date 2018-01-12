---
title: "Интерфейс IWefDebuggingSupport | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b132c51e12d553bcd6e722e87c8aeee96be5e5c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="iwefdebuggingsupport-interface"></a>Интерфейс IWefDebuggingSupport
  Реализованный в среде отладки, такие как Visual Studio, для упрощения отладки приложений для Office. Приложения Office, такие как Word или Excel, получает этот интерфейс из Visual Studio и затем вызывает методы в интерфейсе в некоторых точках во время сеанса отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Методы  
 В следующей таблице перечислены методы, которые определяет этот интерфейс IWefDebuggingSupport.  
  
|name|Описание:|  
|----------|-----------------|  
|[Метод GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Возвращает сведения о приложениях для Office, которые вставляются автоматически во время отладки.|  
|[Метод SetWefProcessId](../vsto/setwefprocessid-method.md)|Представляет идентификатор процесса, который будет выполняться содержимого Framework расширения Web (WEF).|  
  
  