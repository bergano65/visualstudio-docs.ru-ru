---
title: IDebugDocumentContext2::Compare | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Compare
helpviewer_keywords:
- IDebugDocumentContext2::Compare
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7f09684c5e9587c6e3bb631674e009d0b36f4fc5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189417"
---
# <a name="idebugdocumentcontext2compare"></a>IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Сравнивает этот контекст документа, в указанный массив контекстов документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
