---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cbce46afaa6227f5d15720be8aebd4c60f5f236
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015505"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Этот метод позволяет поставщика порта отображать предупреждение перед пользователь присоединяет к процессу unsafe.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемые значения, как показано ниже:  
  
-   `S_OK`: Присоединение к процессу, безопасно и отображается диалоговое окно без предупреждения.  
  
-   `S_FALSE`: Присоединение может не быть проблемой безопасности и отображается диалоговое окно с предупреждением.  
  
-   `FAILURE`: Присоединение к процессу, завершится ошибкой.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)