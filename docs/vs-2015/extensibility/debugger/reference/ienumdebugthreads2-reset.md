---
title: 'IEnumDebugThreads2:: Reset | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Reset
helpviewer_keywords:
- IEnumDebugThreads2::Reset
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c34ed2ecd98af2858af3ac297bf4eb83f3964436
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147711"
---
# <a name="ienumdebugthreads2reset"></a>IEnumDebugThreads2::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Сбрасывает перечисление на первый элемент.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 После вызова этого метода следующий вызов метода [Next](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md) возвращает первый элемент перечисления.  
  
## <a name="see-also"></a>См. также:  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
