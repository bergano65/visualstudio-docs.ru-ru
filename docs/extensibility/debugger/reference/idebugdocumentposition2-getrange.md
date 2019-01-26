---
title: IDebugDocumentPosition2::GetRange | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db27be140cf47e0d070ba3c4f560a4ad89e68b83
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037269"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Получает диапазон для этой позиции документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
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
 Диапазон, указанный в документе должности точку останова используется модуль отладки (DE) для поиска вперед инструкцию, которая фактически участвует код. Рассмотрим следующий пример кода:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Строка 5 вносит нет кода для отлаживаемой программы. Отладчик, который задает точку останова в строке 5 DE поиска в прямом направлении отведенного для первой строки, содержащей код, отладчик будет указать диапазон, включающий дополнительный кандидат строки, где точки останова можно правильно разместить. DE будет затем поиска в прямом направлении через эти строки до ее найти строку, которая могла бы принять точку останова.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)