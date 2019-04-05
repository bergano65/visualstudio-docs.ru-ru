---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d32cd1222d9c6580efab97f38ff924e320c42b42
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978905"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
-   `FAILURE`: Присоединение к процессу, завершится ошибкой.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
