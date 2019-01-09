---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 893dc36c066426ad1de7346c7ce1fea24b191ba3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090692"
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
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Текущий [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ядра не реализует этот метод.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthorProcedure](../../winscript/reference/iactivescriptauthorprocedure-interface.md)