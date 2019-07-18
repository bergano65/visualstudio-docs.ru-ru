---
title: IActiveScriptAuthor::GetChars | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69cdeb16fa0791b3ff8c0cce4a4e67fe110eefc2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935377"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Возвращает набор символов завершения для запрошенного завершения контекста.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fRequestedList`  
 [in] Контекст, запрошенный завершения.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Запрашивает перечисления левой стороны.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Запрашивает контекст элемента завершения.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Запрашивает список параметров.|  
|SCRIPT_CMPL_COMMIT|0x0004|Запросы на завершение списка параметров.|  
  
 `pbstrChars`  
 [out] Символы, которые соответствуют запрошенного завершения контекста.  
  
|`fRequestedList` Параметр|Возвращаются символы|  
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