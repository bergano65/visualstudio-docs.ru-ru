---
title: IActiveScript::SetScriptSite | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fdf5f3ae84d1a991d67170b5f2b02114b91ee05
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157072"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Информирует обработчик сценариев из [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) сайта интерфейс, предоставленный средой размещения. Вызовите этот метод перед любыми другими [IActiveScript](../../winscript/reference/iactivescript.md) используется методы интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pScriptSite`  
 [in] Адрес сайта узла предоставленный скрипт, связываемое с этим экземпляром обработчика скриптов. Сайт должны назначаться уникально для данного сценария экземпляра ядра; его нельзя использовать совместно с другими обработчиков сценариев.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_FAIL`|Произошла неизвестная ошибка; Обработчик скриптов не удалось завершить инициализацию на сайте.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, сайт уже установлен).|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)