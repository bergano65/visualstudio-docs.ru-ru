---
title: IEnumDebugCustomAttributes::Reset | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCustomAttributes::Reset
helpviewer_keywords:
- IEnumDebugCustomAttributes::Reset
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56be764861c63c7f0ca0d7fc94a3841c4483b2cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugcustomattributesreset"></a>IEnumDebugCustomAttributes::Reset
Сбрасывает последовательность перечисления в начало.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 После вызова этого метода, при следующем вызове [Далее](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) метод возвращает первый элемент перечисления.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Вперед](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)