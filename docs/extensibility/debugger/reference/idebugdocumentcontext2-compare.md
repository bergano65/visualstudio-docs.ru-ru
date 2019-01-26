---
title: IDebugDocumentContext2::Compare | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06fe3b1c2acffa47f7c47f5f9426fb1d07bbf288
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54937838"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Сравнивает этот контекст документа, в указанный массив контекстов документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```csharp  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `compare`  
 [in] Значение из [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) перечисление, указывающее тип выполняемого сравнения.  
  
 `rgpDocContextSet`  
 [in] Массив [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) объекты, представляющие контекстов документа, с которым производится сравнение.  
  
 `dwDocContextSetLen`  
 [in] Длина массива контекстов документа для сравнения.  
  
 `pdwDocContext`  
 [out] Возвращает индекс в `rgpDocContextSet` массив первый контекст документа, который удовлетворяет условию сравнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` Если найдено соответствие. Возвращает `S_FALSE` Если совпадений не найдено. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) объекты, передаваемые в массиве должны реализовываться тот же механизм отладки, который реализует `IDebugDocumentContext2` вызванный объект; в противном случае сравнение будет недопустимым.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)