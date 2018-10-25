---
title: IDebugPortEx2::CanTerminateProcess | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::CanTerminateProcess
helpviewer_keywords:
- IDebugPortEx2::CanTerminateProcess
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5717d5312630c3e9adaac2e1a32fa0d44a3a213
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902338"
---
# <a name="idebugportex2canterminateprocess"></a>IDebugPortEx2::CanTerminateProcess
Определяет, можно ли завершить процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CanTerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```csharp  
HRESULT CanTerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pPortProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) объект, представляющий к завершению процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` Если может быть завершен процесс; в противном случае возвращает `S_FALSE`.  
  
## <a name="see-also"></a>См. также  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)