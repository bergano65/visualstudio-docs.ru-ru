---
title: IScriptNode::GetChild | Документация Майкрософт
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
ms.openlocfilehash: 78b5c84c6ed9b3de9593f0d6ff02df93a0e9ba77
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159118"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Возвращает дочерний элемент, находящийся по указанному индексу в узле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `isn`  
 [in] Индекс дочернего элемента в родительском объекте.  
  
 `ppsn`  
 [out] Адрес переменной, которая получает указатель на `IScriptNode` интерфейс дочернего экземпляра.  
  
 Для `IScriptNode` объекты, представляющие веб-страницы, этот параметр Возвращает объект, содержащий блок сценария.  
  
 Для `IScriptEntry` объектов, указать блок сценария, этот параметр Возвращает объект, задающий функцию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Для `IScriptEntry` объектов, указывающих объект-функцию и для `IScriptScriptlet` объектов, этот метод завершается ошибкой, так как нет дочерних элементов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)