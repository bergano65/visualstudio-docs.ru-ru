---
title: "IScriptScriptlet::GetSubItemName | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptScriptlet.GetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: IScriptScriptlet::GetSubItemName
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 43b8483e8a61c25a3911a35d4721c51f7b558530
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptscriptletgetsubitemname"></a>IScriptScriptlet::GetSubItemName
Возвращает последний идентификатор в полное имя узла объекта сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstr`  
 [out] Если узел для полного имени сценариев имеет более одного уровня `pbstr` возвращает адрес буфера идентификатора на втором уровне.  
  
 Если узел для полного имени сценариев имеет один уровень `pbstr` возвращает адрес буфера идентификатора на первом уровне.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)