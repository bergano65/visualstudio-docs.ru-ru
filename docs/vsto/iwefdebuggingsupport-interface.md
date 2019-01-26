---
title: Интерфейс IWefDebuggingSupport
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 55a09c3db9a47b5bcf22a7faeb891a1f709d244a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865688"
---
# <a name="iwefdebuggingsupport-interface"></a>Интерфейс IWefDebuggingSupport
  Реализуется отладочной среде, такой как Visual Studio, чтобы упростить отладку приложений для Office. Приложение Office, например Word или Excel, получает этот интерфейс из Visual Studio и затем вызывает методы в интерфейсе в определенных точках во время сеанса отладки.  
  
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
|[Метод GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Получает сведения о приложениях для Office, который автоматически вставляются во время отладки.|  
|[Метод SetWefProcessId](../vsto/setwefprocessid-method.md)|Предоставляет идентификатор процесса, в которой выполняются расширения Framework Web (WEF) содержимое.|  
