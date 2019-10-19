---
title: 'IActiveScript:: Жетскриптсите | Документация Майкрософт'
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
ms.openlocfilehash: 567c7b5c1ead5388e6ec9c67d6ab6f9f580adf20
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575748"
---
# <a name="iactivescriptgetscriptsite"></a>IActiveScript::GetScriptSite
Извлекает объект сайта, связанный с обработчиком сценариев Windows.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `iid`  
 окне Идентификатор запрашиваемого интерфейса.  
  
 `ppvSiteObject`  
 заполняет Адрес расположения, получающего указатель интерфейса на объект сайта узла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_NOINTERFACE`|Указанный интерфейс не поддерживается.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`S_FALSE`|Сайт не задан; параметр `ppvSiteObject` имеет значение `NULL`.|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)