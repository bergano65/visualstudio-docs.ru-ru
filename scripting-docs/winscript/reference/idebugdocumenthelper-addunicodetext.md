---
title: 'IDebugDocumentHelper:: Аддуникодетекст | Документация Майкрософт'
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
ms.openlocfilehash: 5820c380c92f2c3cd95763b440d5f9755db3e717
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577057"
---
# <a name="idebugdocumenthelperaddunicodetext"></a>IDebugDocumentHelper::AddUnicodeText
Добавляет строку Юникода в конец документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddUnicodeText(  
   LPCOLESTR  pszText  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszText`  
 окне Указатель на строку с завершающим нулем, содержащую текст.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Методу не удалось добавить символы.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод создает `IDebugDocumentTextEvents` уведомления.  
  
> [!NOTE]
> Если этот метод вызывается после вызова `AddDeferredText`, возвращается `E_FAIL`.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)  
 [IDebugDocumentHelper:: адддеферредтекст](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [Интерфейс IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)