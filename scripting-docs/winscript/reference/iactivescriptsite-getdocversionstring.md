---
title: "IActiveScriptSite::GetDocVersionString | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Извлекает строкой, определяемой узла, который уникально идентифицирует версию текущего документа. Если связанный документ был изменен за пределами области сценариев Windows (как в случае HTML-страницы, редактируемого в блокноте), обработчик скриптов можно сохранить вместе с его сохраненного состояния, принудительная перекомпиляция очередного загрузки скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrVersionString`  
 [out] Адрес строки версии определяемого узла документа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_NOTIMPL` , если этот метод не поддерживается.  
  
## <a name="remarks"></a>Примечания  
 Если `E_NOTIMPL` возвращается, обработчик сценариев следует предполагать, что сценарий находится синхронизацию с документом.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)