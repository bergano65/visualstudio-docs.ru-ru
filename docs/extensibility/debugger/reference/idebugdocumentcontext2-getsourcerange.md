---
title: IDebugDocumentContext2::GetSourceRange | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe2ad435b4b70f2314822414c0cc0eb429c2478e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841559"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Получает исходный диапазон кода данного контекста документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pBegPosition`  
 [in, out] Объект [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структуры, который заполняется положением. Установите этот аргумент со значением null, если эта информация не требуется.  
  
 `pEndPosition`  
 [in, out] Объект [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структуры, который заполняется конечную позицию. Установите этот аргумент со значением null, если эта информация не требуется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Исходный диапазон является весь диапазон исходного кода, сзади текущей инструкции сразу же после предыдущей инструкции, использованное кода. Исходный диапазон обычно используется для смешивания исходные инструкции, включая комментарии, с помощью кода в окне дизассемблирования.  
  
 Чтобы получить диапазон для только что код инструкций, содержащихся в данном контексте документ, вызовите [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)