---
title: 'Иактивескриптаусор:: root | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetRoot
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetRoot
ms.assetid: 8e55a0c0-dd35-43d5-bf6f-e2f59c1e88d1
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca2aab154d56cd98c3c2acede61f86f725ce9c1b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576191"
---
# <a name="iactivescriptauthorgetroot"></a>IActiveScriptAuthor::GetRoot
Возвращает `IScriptNode` корень дерева скрипта автора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetRoot(  
   IScriptNode        **ppsp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppsp`  
 заполняет Адрес переменной, которая получает указатель на интерфейс `IScriptNode` корневого узла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иактивескриптаусор](../../winscript/reference/iactivescriptauthor-interface.md)  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)