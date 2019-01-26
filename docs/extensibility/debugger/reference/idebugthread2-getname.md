---
title: IDebugThread2::GetName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f28726afd6dad7c193d552cd05e4c9a9335fef1b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951902"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Возвращает имя потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetName (   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName (   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrName`  
 [out] Возвращает имя потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Полученный именем всегда является имя, которое может отображаться, и это имя Описание потока. Имя потока может быть производным от архитектуры среды выполнения, что поддерживает именованные потоки, или его имя на основе обработчика отладки. Кроме того, можно задать имя потока, с помощью вызова [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)