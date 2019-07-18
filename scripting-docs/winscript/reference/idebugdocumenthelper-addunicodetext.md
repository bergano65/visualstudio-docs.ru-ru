---
title: IDebugDocumentHelper::AddUnicodeText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddUnicodeText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddUnicodeText
ms.assetid: f4ef648e-c55d-4ef0-8df3-e808b798d3b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391095acc1d2f541a3c497abeac5ae7248baa4e8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446629"
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Добавляет строку в Юникоде в конец этого документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszText`  
 [in] Указатель на заканчивающуюся нулем строку, содержащую текст.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Метод не удалось добавить символы.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод создает `IDebugDocumentTextEvents` уведомления.  
  
> [!NOTE]
> Если этот метод вызывается после `AddDeferredText` был вызван, `E_FAIL` возвращается.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Интерфейс IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)