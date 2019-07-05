---
title: IActiveScript::GetScriptSite | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b57c4282b7ec77eb4af2ffa983479ae77388e1c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935775"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Извлекает объект узла, связанный с обработчик скриптов Windows.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `iid`  
 [in] Идентификатор запрашиваемого интерфейса.  
  
 `ppvSiteObject`  
 [out] Адрес расположения, получающей указатель интерфейса на объект главного приложения сайта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_NOINTERFACE`|Указанный интерфейс не поддерживается.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`S_FALSE`|Сайт не был задан; `ppvSiteObject` параметр имеет значение `NULL`.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)