---
title: IDebugDocumentContext2::Compare | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 550695aa52f1c913b25fc56975eb5c6e36b4c091
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
Сравнивает этот контекст документа документ контекстов в указанный массив.  
  
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
 [in] Значение из [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) перечисления, которое указывает тип сравнения.  
  
 `rgpDocContextSet`  
 [in] Массив [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) объекты, представляющие контекстов документа по сравнению с.  
  
 `dwDocContextSetLen`  
 [in] Длина массива контекстов документа для сравнения.  
  
 `pdwDocContext`  
 [out] Возвращает индекс в `rgpDocContextSet` массив контекст первый документ, который удовлетворяет условию сравнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` Если найдено соответствие. Возвращает `S_FALSE` , если соответствие не найдено. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) объекты, передаваемые в массиве должен быть реализован один и тот же механизм отладки, реализующего `IDebugDocumentContext2` объекта вызова; в противном случае, сравнение не является допустимым.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)