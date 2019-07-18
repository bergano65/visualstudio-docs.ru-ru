---
title: IDebugThread2::GetName | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 509db8c30aabd8a4163ea433bb06a99d4bfa2fb9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68153044"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
