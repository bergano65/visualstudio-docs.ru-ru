---
title: 'Искриптноде:: Child | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573555"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Возвращает дочерний элемент, расположенный по указанному индексу в узле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `isn`  
 окне Индекс дочернего элемента в родительском элементе.  
  
 `ppsn`  
 заполняет Адрес переменной, которая получает указатель на интерфейс `IScriptNode` дочернего экземпляра.  
  
 Для `IScriptNode` объектов, представляющих веб-страницу, этот параметр возвращает объект, содержащий блок скрипта.  
  
 Для `IScriptEntry` объектов, указывающих блок скрипта, этот параметр возвращает объект, указывающий функцию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Для `IScriptEntry` объектов, указывающих объект функции и для `IScriptScriptlet` объектов, этот метод завершается ошибкой, так как отсутствуют дочерние записи.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)