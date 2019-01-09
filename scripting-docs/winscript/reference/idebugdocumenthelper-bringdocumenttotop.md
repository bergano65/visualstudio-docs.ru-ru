---
title: IDebugDocumentHelper::BringDocumentToTop | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.BringDocumentToTop
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::BringDocumentToTop
ms.assetid: 91bdbb05-6f79-4b07-a707-838cb75a770f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4992b68d0644e6183e62577bdec9be86f50df592
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086961"
---
# <a name="idebugdocumenthelperbringdocumenttotop"></a>IDebugDocumentHelper::BringDocumentToTop
Привносит в этом документе отладчик в верхнюю часть пользовательского интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT BringDocumentToTop();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод запускает отладчик, если она еще не запущена.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)