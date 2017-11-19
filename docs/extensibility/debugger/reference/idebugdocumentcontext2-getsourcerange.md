---
title: "IDebugDocumentContext2::GetSourceRange | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2::GetSourceRange
helpviewer_keywords: IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3fc08e761b3944aafd2303bd7266c98dc06e1be8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Возвращает диапазон код исходного контекста этого документа.  
  
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
 [in, out] Объект [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структуру, которая заполняется начальную позицию. Задайте этот аргумент со значением null, если эта информация не требуется.  
  
 `pEndPosition`  
 [in, out] Объект [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) структуру, которая заносится в текущем положении. Задайте этот аргумент со значением null, если эта информация не требуется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Исходный диапазон является весь диапазон исходного кода из текущей резервной инструкции сразу же после предыдущей инструкции, использованное кода. Исходный диапазон обычно используется при смешивании исходного кода, включая комментарии, с помощью кода в окне дизассемблирования.  
  
 Чтобы получить диапазон для только что исходный код инструкций, содержащихся в этом контексте документа, вызовите [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)