---
title: 'Иактивескриптаусор:: Жетлангуажефлагс | Документация Майкрософт'
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
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576203"
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
 заполняет Флаги, содержащие сведения о языке. Может быть сочетанием следующих значений:  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|фасапреферинтерналхандлер|0x0001|Язык предпочитает создание обработчика событий сценария обработчиком создания скриптов, а не приложением.|  
|фасасуппортинтерналхандлер|0x0002|Язык поддерживает обработчики событий скриптов, созданные обработчиком создания скриптов.|  
|фасакасесенситиве|0x0004|В языке сценариев учитывается регистр.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Если обработчик создания скриптов управляет обработчиками событий, приложение должно вызывать `CreateChildHandler` из объекта `IScriptEntry`. При этом создается объект `IScriptScriptlet`, соответствующий обработчику событий. Обработчик также добавляет обработчик событий в запись скрипта. Обработчик событий — это пустая функция, которая содержит указанные сведения о подписи.  
  
 Если приложение управляет обработчиками событий, оно должно вызывать `CreateChildHandler` из объекта `IScriptNode`, который представляет обработчик событий скриптлет. При этом создается объект `IScriptScriptlet`, связанный с обработчиком событий скриптлет. Приложение также должно добавить пустую функцию в качестве обработчика событий в новый или существующий объект `IScriptEntry`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)