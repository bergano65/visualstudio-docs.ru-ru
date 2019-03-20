---
title: IDebugDocumentText::GetLineOfPosition | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetLineOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetLineOfPosition
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d5d33a68b4bc87307281e37ff96f84834257a22
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156012"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
Возвращает номер строки и, возможно, смещение знака в строке, соответствующей в данную позицию символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cCharacterPosition`  
 [in] Местоположение символа диапазона позиции начала.  
  
 `pcLineNumber`  
 [out] Номер строки в диапазоне.  
  
 `pcCharacterOffsetInLine`  
 [in, out] Смещение знаков объекта диапазона, в строке `pcLineNumber`. Если этот параметр равен `NULL`, метод возвращает значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает номер строки и, возможно, смещение знака в строке, соответствующей в данную позицию символа.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)