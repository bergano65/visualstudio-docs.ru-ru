---
title: 'Идебугдокументинфо:: Жетдокументклассид | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 996e6d751807bba1e1a74cbb7e579db25193c32b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569080"
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
Возвращает `CLSID`, определяющую тип документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pclsidDocument`  
 заполняет @No__t_0, определяющий тип документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод позволяет интегрированной среде разработки отладчика размещать пользовательские средства просмотра для этого документа.  
  
 Если в документе нет отображаемых данных, возвращаемое значение `pclsidDocument` будет `CLSID_NULL`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)