---
title: Интерфейс IWefDebuggingSupport | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8e8a1bc770ce030902691a8ee4f2634c79cbab9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
|name|Описание|  
|----------|-----------------|  
|[Метод GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Возвращает сведения о приложениях для Office, которые вставляются автоматически во время отладки.|  
|[Метод SetWefProcessId](../vsto/setwefprocessid-method.md)|Представляет идентификатор процесса, который будет выполняться содержимого Framework расширения Web (WEF).|  
  
  