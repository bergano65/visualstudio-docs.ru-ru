---
title: IScriptNode::GetChild | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 55cd6cf5233e850e4109128e322d3fc5bd0b1355
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086597"
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