---
title: "IDebugDocumentInfo::GetName | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentInfo.GetName
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da369c328c2f92915c60b1c50517938bf76d5202
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
Возвращает имя указанного документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dnt`  
 [in] Тип возвращаемого имени документа.  
  
 `pbstrName`  
 [out] Строка, содержащая имя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Указанное имя документа не известен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает имя указанного документа.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugDocumentInfo](../../winscript/reference/idebugdocumentinfo-interface.md)   
 [Перечисление DOCUMENTNAMETYPE](../../winscript/reference/documentnametype-enumeration.md)