---
title: "IDebugDocumentTextExternalAuthor::NotifyChanged | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 016eda303f5a5a74a20e42112890698a1ca28798
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
Уведомляет основное приложение об изменении исходного документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается методом внешний редактор после документа отладчик на основе файла изменены и сохранены для уведомления узла об изменении документа источника. Узел обновит документа из исходного файла.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)