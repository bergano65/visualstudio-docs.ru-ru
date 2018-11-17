---
title: IDebugDocumentPositionOffset2::GetRange | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eca754c3154267629a1d6567c3412ec44a0784f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809250"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает диапазон для текущей позиции документа.  
  
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
 [in, out] Смещение для начальное положение диапазона. Установите этот параметр в значение null, если эта информация не требуется.  
  
 `pdwEndOffset`  
 [in, out] Смещение для конечное положение диапазона. Установите этот параметр в значение null, если эта информация не требуется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Диапазон, указанный в документе должности точку останова используется модуль отладки (DE) для поиска вперед инструкцию, которая фактически участвует код. Рассмотрим следующий пример кода:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Строка 5 вносит нет кода для отлаживаемой программы. Отладчик, который задает точку останова в строке 5 DE поиска в прямом направлении отведенного для первой строки, содержащей код, отладчик будет указать диапазон, включающий дополнительный кандидат строки, где точки останова может быть правильно расположены. DE будет затем поиска в прямом направлении через эти строки до ее найти строку, которая могла бы принять точку останова.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)

