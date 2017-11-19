---
title: "IScriptScriptlet::SetSubItemName | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptScriptlet.SetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: IScriptScriptlet::SetSubItemName
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0d038330d502dd9a230fdb82c14d36732fed7e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptletsetsubitemname"></a>IScriptScriptlet::SetSubItemName
Задает идентификатор последнего в полное имя узла объекта сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `psz`  
 Если узел для полного имени сценариев имеет более одного уровня `psz` адрес буфера идентификатора на втором уровне.  
  
 Если узел для полного имени сценариев имеет один уровень `psz` адрес буфера идентификатора на первом уровне.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)