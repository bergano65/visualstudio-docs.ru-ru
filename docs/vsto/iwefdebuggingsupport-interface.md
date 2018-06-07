---
title: Интерфейс IWefDebuggingSupport
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
ms.openlocfilehash: 351fb69b99393a10518168f4f9b01efe1f9efaa7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572677"
---
# <a name="iwefdebuggingsupport-interface"></a>Интерфейс IWefDebuggingSupport
  Реализованный в среде отладки, такие как Visual Studio, для упрощения отладки приложений для Office. Приложения Office, такие как Word или Excel, получает этот интерфейс из Visual Studio и затем вызывает методы в интерфейсе в некоторых точках во время сеанса отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp 
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
  
  