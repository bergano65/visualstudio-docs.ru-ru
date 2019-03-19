---
title: IDebugDocumentHelper::Attach | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f4fbd1686d27e594b748ca97c82c645de1b93de
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151210"
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Добавляет в этом документе в дереве документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pddhParent`  
 [in] Дерево документов, куда будет добавлен в этом документе. Может иметь значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод добавляет в этом документе к документу дерева, с помощью `pddhParent` как родительский. Если `pddhParent` является `NULL`, этот документ будет документ верхнего уровня.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)