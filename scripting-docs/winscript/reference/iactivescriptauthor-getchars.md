---
title: 'Иактивескриптаусор:: GetChars | Документация Майкрософт'
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
ms.openlocfilehash: 2ce2b46d65c2ce92111bc4b6f44f66ce9dc4ce5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576254"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Возвращает набор символов завершения для запрошенного контекста завершения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `fRequestedList`  
 окне Запрошенный контекст завершения.  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|Запрашивает перечисление слева.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|Запрашивает контекст завершения элемента.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Запрашивает список параметров.|  
|SCRIPT_CMPL_COMMIT|0x0004|Запрашивает завершение списка параметров.|  
  
 `pbstrChars`  
 заполняет Символы, соответствующие запрошенному контексту завершения.  
  
|`fRequestedList`, параметр|Возвращенные символы|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)