---
title: IEnumDebugPrograms2::Reset | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPrograms2::Reset
helpviewer_keywords:
- IEnumDebugPrograms2::Reset
ms.assetid: b289242b-24ea-4df3-a811-20b0c8a903d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 88d95b58f429c8a6012769166bf740f06675a994
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905391"
---
# <a name="ienumdebugprograms2reset"></a>IEnumDebugPrograms2::Reset
Выполняет сброс перечисления к первому элементу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 После вызова этого метода, следующий вызов [Далее](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md) метод возвращает первый элемент перечисления.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)