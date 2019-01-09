---
title: IDebugDocumentInfo::GetName | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: f3ecde4fbde1a265596a01d7f0f953763363e797
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097699"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Возвращает имя указанного документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dnt`  
 [in] Тип имени для возврата.  
  
 `pbstrName`  
 [out] Строка, содержащая имя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Указанное имя документа не известна.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает имя указанного документа.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Перечисление DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)