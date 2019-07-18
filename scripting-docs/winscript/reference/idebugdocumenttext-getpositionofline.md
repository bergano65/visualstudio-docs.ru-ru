---
title: IDebugDocumentText::GetPositionOfLine | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfLine
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfLine
ms.assetid: d1e6e81b-ddec-4a7c-9b6a-d199e3debfc2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4cfcfc771c49abbf837f4db898936e478cda2194
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970852"
---
# <a name="idebugdocumenttextgetpositionofline"></a>IDebugDocumentText::GetPositionOfLine
Возвращает позицию символа, соответствующего до первого символа строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetPositionOfLine(  
   ULONG   cLineNumber,  
   ULONG*  pcCharacterPosition  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cLineNumber`  
 [in] Номер строки.  
  
 `pcCharacterPosition`  
 [out] Положение знака в документе в начало строки `cLineNumber`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает позицию символа, соответствующего до первого символа строки.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)