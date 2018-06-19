---
title: IActiveScript::GetScriptSite | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptSite
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptSite
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 961483d45c72018bc216306d6c1aba0400a367ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640374"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Извлекает объект узла, связанный с обработчиком сценариев Windows.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `iid`  
 [in] Идентификатор запрашиваемого интерфейса.  
  
 `ppvSiteObject`  
 [out] Адрес расположения, получающей указатель интерфейса на объект сайта поставщика услуг размещения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_NOINTERFACE`|Указанный интерфейс не поддерживается.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`S_FALSE`|Сайт не был задан; `ppvSiteObject` параметра равным `NULL`.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)