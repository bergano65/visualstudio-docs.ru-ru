---
title: "IActiveScriptAuthor::GetChars | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abc9c819c2dd4a75d6223af86b4fe89baebc186b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Возвращает набор символов завершения для завершения запрошенной контекста.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fRequestedList`  
 [in] Контекст выполнения запрошенного.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Запрашивает перечисления левой стороны.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Запрашивает контекст выполнения элемента.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Запрашивает список параметров.|  
|SCRIPT_CMPL_COMMIT|0x0004|Запросы на завершение списка параметров.|  
  
 `pbstrChars`  
 [out] Символы, которые соответствуют запрошенного завершения контекста.  
  
|`fRequestedList`параметр|Возвращаются символы|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)