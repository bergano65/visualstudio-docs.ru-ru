---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Документы Microsoft
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
ms.openlocfilehash: b9c4a1ba03a8498dbaa857dc5dbabba8914e54a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645644"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
Выполняет синтаксический анализ кода процедура добавляет текст процедуры код сценария, модуль создания и создает `IScriptEntry` объект, соответствующий код процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Анализируемый текст сценария.  
  
 `pszFormalParams`  
 [in] Адрес имена формальных параметров для процедуры. Имена параметров должны быть разделены соответствующие разделители для создания обработчика сценария. Имена не должны заключаться в круглые скобки.  
  
 `pszProcedureName`  
 [in] Адрес имени процедуры для синтаксического анализа.  
  
 `pszItemName`  
 [in] Адрес буфера, который содержит имя элемента связанные с `IScriptEntry` объекта.  
  
 `pszDelimiter`  
 [in] Адрес разделитель end из скрипта блока. Когда `pszCode` анализируется из текстового потока, узел обычно использует разделитель (например, две одинарных кавычки), для определения конца блока скрипта. Установите этот параметр значение NULL, если разделитель не для обозначения конца блока скрипта.  
  
 `dwCookie`  
 [in] Определяемые приложением значения, связанного с новым `IScriptEntry` объекта.  
  
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