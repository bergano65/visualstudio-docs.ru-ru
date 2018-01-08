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
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 150c8794fb35ca017be7e0873dc0d1b84ebfc38c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
  