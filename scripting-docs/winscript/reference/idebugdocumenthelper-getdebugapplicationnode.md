---
title: IDebugDocumentHelper::GetDebugApplicationNode | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetDebugApplicationNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetDebugApplicationNode
ms.assetid: ecd18803-beb4-4ac2-9702-cc9e8a12c395
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10740c3489b617b1685ad222cac7c158e0196c4d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146257"
---
# <a name="idebugdocumenthelpergetdebugapplicationnode"></a>IDebugDocumentHelper::GetDebugApplicationNode
Возвращает узел отладки приложения, соответствующий этому документу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDebugApplicationNode(  
   IDebugApplicationNode**  ppdan  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppdan`  
 [out] Узел отладки приложения, соответствующий этому документу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Возвращает узел отладки приложения, соответствующий этому документу.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)