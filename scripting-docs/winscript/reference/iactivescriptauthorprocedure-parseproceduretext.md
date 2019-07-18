---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
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
ms.openlocfilehash: c513b105a483d0f80510dff9c91fa2c3f09e0523
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955163"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Выполняет синтаксический анализ кода процедуры, добавляется текст процедуры код сценария разработки ядра и создает `IScriptEntry` объект, соответствующий код процедуры.  
  
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
 [in] Анализируемый текст скрипта.  
  
 `pszFormalParams`  
 [in] Адрес имена формальных параметров для процедуры. Имена параметров должны быть разделены соответствующие разделители для сценария создания ядра. Имена не должны заключаться в круглые скобки.  
  
 `pszProcedureName`  
 [in] Адрес имя процедуры, который необходимо проанализировать.  
  
 `pszItemName`  
 [in] Адрес буфера, который содержит имя элемента связан `IScriptEntry` объекта.  
  
 `pszDelimiter`  
 [in] Адрес-объекта блок сценариев end разделитель. Когда `pszCode` анализируется из потока текста узел обычно использует разделитель (например, две одинарные кавычки), чтобы обнаружить завершение блока скрипта. Установите этот параметр значение NULL, если разделитель не для обозначения конца блока скрипта.  
  
 `dwCookie`  
 [in] Определяемое приложением значение, которая связана с новым `IScriptEntry` объекта.  
  
 `dwFlags`  
 [in] Не используется.  
  
 `pdispFor`  
 [in] Не используется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Текущий [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ядра не реализует этот метод.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)