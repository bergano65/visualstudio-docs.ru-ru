---
title: IDebugThread2::GetName | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 670ee7b9fe8262e981f3c0abeb57710c2da9b0e2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898477"
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