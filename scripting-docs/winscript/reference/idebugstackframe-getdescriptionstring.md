---
title: IDebugStackFrame::GetDescriptionString | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetDescriptionString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f870c6dbc654f8465d201c53443228153ce4a68b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152841"
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Возвращает короткое или долго текстовое описание кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fLong`  
 [in] Флаг, где `TRUE` возвращает подробное описание и `FALSE` возвращает краткое описание.  
  
 `pbstrDescription`  
 [out] Описание кадра стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Как правило если `fLong` является `FALSE`, этот метод предоставляет только имя функции, связанные с этим кадром стека. Когда `fLong` является `TRUE`, этот метод также может предоставлять параметров функции и другие необходимые сведения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)