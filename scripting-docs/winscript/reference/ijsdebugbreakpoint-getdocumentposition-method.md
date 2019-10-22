---
title: 'Метод метод ijsdebugbreakpoint:: Жетдокументпоситион | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.GetDocumentPosition
apilocation:
- jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f3bc5aff0b7079e20e2bcd49189153d2ec20d9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577692"
---
# <a name="ijsdebugbreakpointgetdocumentposition-method"></a>Метод IJsDebugBreakPoint::GetDocumentPosition
Возвращает позицию инструкции, в которой была привязана точка останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDocumentId`  
 заполняет Уникальный идентификатор исходного документа (указатель на Идебугдокументтекст).  
  
 `pCharacterOffset`  
 заполняет Отсчитываемое от нуля смещение символов от начала скрипта.  
  
 `pStatementCharCount`  
 заполняет Длина текущего оператора, начинающегося в * Пчарактероффсет, в символах.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugBreakPoint](../../winscript/reference/ijsdebugbreakpoint-interface.md)