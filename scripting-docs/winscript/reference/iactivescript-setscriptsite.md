---
title: IActiveScript::SetScriptSite | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b2a96732e904c7249dc5228ef414c3315012ec56
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097439"
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