---
title: 'Идебугпроцесссекурити:: Куерикансафеляттач | Документация Майкрософт'
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
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187960"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод позволяет поставщику порта отображать предупреждение перед присоединением пользователя к незащищенному процессу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Ниже приведены возвращаемые значения.  
  
- `S_OK`: Присоединение к процессу является надежным, и не отображается диалоговое окно предупреждения.  
  
- `S_FALSE`: Присоединение может быть проблемой безопасности, и отображается диалоговое окно с предупреждением.  
  
- `FAILURE`: Присоединение к процессу завершается ошибкой.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
