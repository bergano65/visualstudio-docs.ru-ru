---
title: IDebugDocumentHelper::BringDocumentContextToTop | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.BringDocumentContextToTop
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::BringDocumentContextToTop
ms.assetid: cf9751c5-e9b7-45c6-b084-3f3873dbf01d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41452331d03fdca53c8c7048a24adfd349c128ad
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144554"
---
# <a name="idebugdocumenthelperbringdocumentcontexttotop"></a>IDebugDocumentHelper::BringDocumentContextToTop
Предоставляет контекст этого документа в начало в пользовательском интерфейсе отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pddc`  
 Контекст документа, чтобы переместить наверх в пользовательском интерфейсе отладчика.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод обеспечивает контекст этого документа в начало в пользовательском интерфейсе отладчика.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)