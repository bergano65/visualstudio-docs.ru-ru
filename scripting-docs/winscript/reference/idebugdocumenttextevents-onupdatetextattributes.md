---
title: "IDebugDocumentTextEvents::onUpdateTextAttributes | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentTextEvents::onUpdateTextAttributes
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ea7caa1c1632e1a85e12010ec39593b8e0a6d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttexteventsonupdatetextattributes"></a>IDebugDocumentTextEvents::onUpdateTextAttributes
Указывает, что изменились текст атрибуты, связанные с базовой позиции диапазона знаков.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cCharacterPosition`  
 [in] Позиция символа первого символа, что изменились атрибуты.  
  
 `cNumToUpdate`  
 [in] Число символов в диапазоне.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод указывает, что изменились текст атрибуты, связанные с базовой позиции диапазона знаков.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)