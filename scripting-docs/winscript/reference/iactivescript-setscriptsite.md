---
title: 'IActiveScript:: Сетскриптсите | Документация Майкрософт'
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
ms.openlocfilehash: 063dcc7b580334bff9780e9c209b621ef7e25656
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575332"
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Информирует обработчик скриптов о сайте интерфейса [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) , предоставленном узлом. Вызовите этот метод перед использованием любых других методов интерфейса [IActiveScript](../../winscript/reference/iactivescript.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pScriptSite`  
 окне Адрес сайта скрипта, предоставляемого узлом, который должен быть связан с этим экземпляром обработчика скриптов. Сайт должен быть однозначно назначен этому экземпляру обработчика сценариев; Он не может использоваться совместно с другими обработчиками сценариев.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_FAIL`|Произошла неопределенная ошибка; обработчику скриптов не удалось завершить инициализацию сайта.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, сайт уже задан).|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)