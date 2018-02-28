---
title: "IActiveScriptAuthor::GetLanguageFlags | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Возвращает сведения о языке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pgrfasa`  
 [out] Флаги, которые содержат сведения о языке. Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Язык является предпочтительным скрипт создания обработчика событий с помощью скрипта создания ядра вместо приложения.|  
|fasaSupportInternalHandler|0x0002|Язык поддерживает сценарий обработчики событий, создаваемые сценарием разработки ядра.|  
|fasaCaseSensitive|0x0004|Язык скриптов учитывается регистр символов.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Если скрипт создания engine управляет обработчики событий, приложение должно вызывать `CreateChildHandler` из `IScriptEntry` объекта. При этом создается `IScriptScriptlet` объект, соответствующий обработчик событий. Среда также добавляет обработчик событий запись скрипта. Обработчик событий — это пустой функция, которая содержит сведения о указанной подписи.  
  
 Если приложение управляет обработчики событий, он должен вызывать `CreateChildHandler` из `IScriptNode` , представляющий событие обработчика сценариев. При этом создается `IScriptScriptlet` объекта, связанного с сценариев обработчика событий. Приложение также должен добавить пустую функцию как событие обработчика в новую или существующую `IScriptEntry` объекта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)