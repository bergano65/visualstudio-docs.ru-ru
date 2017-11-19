---
title: "IScriptEntry::GetBody | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetBody
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9daa04009cf7088cbd21a2d3dfa185f581c157a3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Возвращает текст, соответствующий текст `IScriptEntry` блок сценария, функции или сценариев.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstr`  
 [out] Текст, который находится в теле одного из следующих действий:  
  
-   `IScriptEntry` Блок сценария  
  
-   `IScriptEntry` Функции в блоке, функция  
  
-   `IScriptEntry` Обработчик сценариев  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)