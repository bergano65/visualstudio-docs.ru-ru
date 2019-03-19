---
title: IDebugDocumentHelper::SetDocumentAttr | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetDocumentAttr
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetDocumentAttr
ms.assetid: bd7ffdbd-de51-477d-bd3f-760db020fe70
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3c19e5b2091bf9dd30359f30e27019fa778b675
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149212"
---
# <a name="idebugdocumenthelpersetdocumentattr"></a>IDebugDocumentHelper::SetDocumentAttr
Задает атрибуты для этого документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetDocumentAttr(  
   TEXT_DOC_ATTR  pszAttributes  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszAttributes`  
 [in] Атрибуты, применяемые к документу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод задает атрибуты для этого документа.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Константы TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)