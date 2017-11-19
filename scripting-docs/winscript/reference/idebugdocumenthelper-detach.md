---
title: "IDebugDocumentHelper::Detach | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.Detach
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::Detach
ms.assetid: 820b9a8c-9a88-479a-b095-daea99394f9c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5abfe1aeba6eb7435e72797f0739c9abc7b5ff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperdetach"></a>IDebugDocumentHelper::Detach
Удаляет этот документ из дерева документов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод удаляет этот документ в дереве документа.  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)