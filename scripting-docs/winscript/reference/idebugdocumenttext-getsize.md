---
title: "IDebugDocumentText::GetSize | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentText.GetSize
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3152150c46793a71ec7a46b6ab2097efa06f6fc8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
Возвращает число строк и число символов в документе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcNumLines`  
 [out] Число строк в документе. Если этот параметр имеет значение NULL, метод не возвращает значение.  
  
 `pcNumChars`  
 [out] Число символов в документе. Если этот параметр имеет значение NULL, метод не возвращает значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает число строк и число символов в документе.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)