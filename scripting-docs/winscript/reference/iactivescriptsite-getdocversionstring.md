---
title: 'IActiveScriptSite:: Жетдокверсионстринг | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571133"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Извлекает определяемую узлом строку, уникально идентифицирующую текущую версию документа. Если связанный документ изменился вне области сценария Windows (как в случае HTML-страницы, редактируемой с помощью Блокнота), обработчик сценариев может сохранить его вместе с сохраненным состоянием, принудительно перекомпилировать при следующем запуске скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrVersionString`  
 заполняет Адрес строки версии документа, определяемой узлом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успеха или `E_NOTIMPL`, если этот метод не поддерживается.  
  
## <a name="remarks"></a>Заметки  
 Если возвращается `E_NOTIMPL`, обработчик сценариев должен предположить, что сценарий синхронизирован с документом.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)