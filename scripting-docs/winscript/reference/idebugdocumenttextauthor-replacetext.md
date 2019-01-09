---
title: IDebugDocumentTextAuthor::ReplaceText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextAuthor.ReplaceText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextAuthor::ReplaceText
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 579d0ef243de7cd9bfcb821e75aa5ca213712a88
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090601"
---
# <a name="idebugdocumenttextauthorreplacetext"></a>IDebugDocumentTextAuthor::ReplaceText
Заменяет текст в документе.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cCharacterPosition`  
 [in] Запустите расположение диапазона символов для замены.  
  
 `cNumToReplace`  
 [in] Число символов для замены.  
  
 `pcharText[]`  
 [in] Буфер, содержащий новые символы для замены старого символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод заменяет текст в документе.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentTextAuthor](../../winscript/reference/idebugdocumenttextauthor-interface.md)