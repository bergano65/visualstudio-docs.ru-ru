---
title: IDebugDocumentContext2::Compare | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d440f585cca5b531fbd97cbbfe6b1ff852cec9d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744905"
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

