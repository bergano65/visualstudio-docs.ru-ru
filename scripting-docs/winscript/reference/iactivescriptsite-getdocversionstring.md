---
title: IActiveScriptSite::GetDocVersionString | Документация Майкрософт
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
ms.openlocfilehash: 7327b71329c1f476eab9c27d5e0d5a047664abfa
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147960"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Извлекает строку, однозначно определяющее текущую версию документа определяемого узла. Если связанный документ был изменен вне области сценариев Windows (как в случае HTML-страницы, редактируемого в блокноте), обработчик сценариев можно сохранить вместе с его сохраненное состояние, принудительной повторной компиляции в следующий раз загрузки скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pstrVersionString`  
 [out] Адрес строки версии документа, определенного узла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` в случае успешного выполнения или `E_NOTIMPL` Если этот метод не поддерживается.  
  
## <a name="remarks"></a>Примечания  
 Если `E_NOTIMPL` возвращается, обработчик скриптов следует полагать, что сценарий является синхронизовано с документом.  
  
## <a name="see-also"></a>См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)