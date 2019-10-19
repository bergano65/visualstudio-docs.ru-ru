---
title: 'Иактивескриптаусор:: методы removenameditem | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cade532d2ca276237981855cafe12804307d0bb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572842"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
Удаляет объект `NamedItem` из пространства имен обработчика создания скриптов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszName`  
 окне Адрес буфера, определяющий удаляемый объект `NamedItem`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
|`S_FALSE`|Объект `NamedItem` отсутствует в пространстве имен обработчика создания скриптов.|  
  
## <a name="remarks"></a>Заметки  
 [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) используется для вставки объекта `NamedItem` в пространство имен механизма разработки скриптов.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иактивескриптаусор](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)