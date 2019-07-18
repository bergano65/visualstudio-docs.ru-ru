---
title: IDebugDocumentTextExternalAuthor::NotifyChanged | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1290de76f8bec5018ad83eb4499c3d92cbf9eba9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978540"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
Уведомляет ведущее приложение об изменении исходного документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается внешним редактором, после изменения и сохранения для уведомления узла об изменении источник документа документ отладчика на основе файлов. Узел обновит документа из исходного файла.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentTextExternalAuthor](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)