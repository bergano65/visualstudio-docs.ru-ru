---
title: IScriptNode::GetParent | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c990b5ba5c3d03d319e0eeced282c92cfbb5281
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786860"
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Возвращает `IScriptNode` объект, являющийся родительским для объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppsnParent`  
 [out] Адрес переменной, которая получает указатель на `IScriptNode` интерфейс родительского экземпляра.  
  
 Если класс реализует `IScriptEntry` или `IScriptScriptlet`, `IScriptNode` , то возвращается объект.  
  
 Если класс реализует `IScriptNode` (представляющие веб-страницы), возвращается значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)