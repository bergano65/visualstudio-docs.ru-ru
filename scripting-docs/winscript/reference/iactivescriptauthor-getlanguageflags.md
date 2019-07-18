---
title: IActiveScriptAuthor::GetLanguageFlags | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9f1a68db05ac0d909108ce77587ae4b071c9a2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935475"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Возвращает сведения о языке.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pgrfasa`  
 [out] Флаги, которые содержат сведения о языке. Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Язык, является предпочтительным для создания обработчика события скрипта с помощью сценария создания ядра вместо приложения.|  
|fasaSupportInternalHandler|0x0002|Язык поддерживает сценарий обработчики событий, создаваемых сценарием разработки ядра.|  
|fasaCaseSensitive|0x0004|Язык скрипта чувствительно к регистру.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Если скрипт создания engine управляет обработчики событий, приложение должно вызывать `CreateChildHandler` из `IScriptEntry` объекта. При этом создается `IScriptScriptlet` объект, соответствующий обработчик событий. Модуль также добавляет обработчик событий к записи скрипта. Обработчик событий — пустая функция с информацией, указанной сигнатурой.  
  
 Если ваше приложение управляет обработчики событий, он должен вызывать `CreateChildHandler` из `IScriptNode` , представляющий обработчик событий скриптлета. При этом создается `IScriptScriptlet` объект, связанный со скриптлетом обработчика событий. Приложение также должно добавить пустую функцию как событие обработчика в новую или существующую `IScriptEntry` объекта.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)