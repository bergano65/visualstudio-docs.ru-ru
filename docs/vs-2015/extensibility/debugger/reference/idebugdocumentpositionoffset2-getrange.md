---
title: 'IDebugDocumentPositionOffset2:: Range | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a028a2c88fe44aa6a117ddb81cff5788eec1732e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200231"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает диапазон для текущего расположения документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwBegOffset`  
 [вход, выход] Смещение начальной позиции диапазона. Если эти сведения не требуются, присвойте этому параметру значение null.  
  
 `pdwEndOffset`  
 [вход, выход] Смещение конечной позиции диапазона. Если эти сведения не требуются, присвойте этому параметру значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Диапазон, указанный в позиции документа для точки останова расположения, используется модулем отладки (DE) для поиска оператора, который фактически участвует в коде. Рассмотрим следующий пример кода:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Строка 5 не вносит код в отлаживаемую программу. Если отладчику, устанавливающему точку останова в строке 5, требуется, чтобы DE выполнял поиск первой строки, которая участвует в коде, отладчик укажет диапазон, включающий дополнительные строки-кандидаты, где точка останова может быть правильно размещена. После этого команда «DE» будет выполнять поиск вперед по этим строкам, пока не найдет строку, которая может принять точку останова.  
  
## <a name="see-also"></a>См. также:  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
