---
title: IDebugDocumentTextEvents::onUpdateDocumentAttributes | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onUpdateDocumentAttributes
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef8791a68086c02b7e1cc8d0a603deba63943af4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946681"
---
# <a name="idebugdocumenttexteventsonupdatedocumentattributes"></a>IDebugDocumentTextEvents::onUpdateDocumentAttributes
Указывает, что изменить атрибуты документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `textdocattr`  
 [in] Новые атрибуты документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод указывает, что изменились атрибуты документа.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [Константы TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)