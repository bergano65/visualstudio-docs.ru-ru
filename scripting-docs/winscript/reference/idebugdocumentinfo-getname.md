---
title: 'Идебугдокументинфо:: Name | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570954"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Возвращает указанное имя документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dnt`  
 окне Тип возвращаемого имени документа.  
  
 `pbstrName`  
 заполняет Строка, содержащая имя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Указанное имя документа неизвестно.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возвращает указанное имя документа.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса идебугдокументинфо](../../winscript/reference/idebugdocumentinfo-interface.md)  
 [Перечисление DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)