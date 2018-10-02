---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 243c8556e38bd89200ca591d4b087e441baf57f1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572937"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProcessSecurity::QueryCanSafelyAttach](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach).  
  
Этот метод позволяет поставщика порта отображать предупреждение перед пользователь присоединяет к процессу unsafe.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемые значения, как показано ниже:  
  
-   `S_OK`: Присоединение к процессу, безопасно и отображается диалоговое окно без предупреждения.  
  
-   `S_FALSE`: Присоединение может не быть проблемой безопасности и отображается диалоговое окно с предупреждением.  
  
-   `FAILURE`: Не удается присоединение к процессу.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

