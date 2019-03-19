---
title: IDebugDocumentProvider::GetDocument | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentProvider.GetDocument
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentProvider::GetDocument
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f6b816f455d213cb81065f1909930bf50eeb415
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146608"
---
# <a name="idebugdocumentprovidergetdocument"></a>IDebugDocumentProvider::GetDocument
В результате документ создаваться, если он еще не существует.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppssd`  
 [out] Документ отладки, относящейся к документу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывает его для создания экземпляра, если он еще не существует.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentProvider](../../winscript/reference/idebugdocumentprovider-interface.md)