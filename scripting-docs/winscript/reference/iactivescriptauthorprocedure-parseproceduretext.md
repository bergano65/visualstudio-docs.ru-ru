---
title: IActiveScriptAuthorProcedure::P Арсепроцедуретекст | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11a34843f30274ec78f1652c5ed5cd4dbcf2884a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572816"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Анализирует процедуру кода, добавляет текст процедуры кода в механизм создания скриптов и создает объект `IScriptEntry`, соответствующий процедуре кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszCode`  
 окне Анализируемый текст скрипта.  
  
 `pszFormalParams`  
 окне Адрес формальных имен параметров для процедуры. Имена параметров должны быть разделены соответствующими разделителями для обработчика создания скриптов. Имена не должны заключаться в круглые скобки.  
  
 `pszProcedureName`  
 окне Адрес имени процедуры для синтаксического анализа.  
  
 `pszItemName`  
 окне Адрес буфера, содержащий имя элемента, связанного с объектом `IScriptEntry`.  
  
 `pszDelimiter`  
 окне Адрес разделителя-блока конца скрипта. Когда `pszCode` анализируется из потока текста, узел обычно использует разделитель (например, две одинарные кавычки) для обнаружения конца блока скрипта. Присвойте этому параметру значение NULL, если нет разделителя для пометки конца блока скрипта.  
  
 `dwCookie`  
 окне Определяемое приложением значение, связанное с новым объектом `IScriptEntry`.  
  
 `dwFlags`  
 окне Не используется.  
  
 `pdispFor`  
 окне Не используется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Текущий обработчик [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] не реализует этот метод.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)