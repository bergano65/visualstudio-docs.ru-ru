---
title: IDebugDocumentHelper::SetLongName | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetLongName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetLongName
ms.assetid: b6199e5d-9b54-43a2-9775-214b8d022607
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 153655966f3be59f1d01fd375b8669fb7207e2d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725914"
---
# <a name="idebugdocumenthelpersetlongname"></a>IDebugDocumentHelper::SetLongName
Задает длинное имя для документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetLongName(  
   LPCOLESTR  pszLongName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszLongName`  
 [in] Нулем строка, содержащая длинное имя документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод устанавливает новое длинное имя для документа.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)