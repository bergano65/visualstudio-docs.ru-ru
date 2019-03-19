---
title: IScriptEntry::GetBody | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a2cb9757c0a9683a00768d8947dfe33749e4bb9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147947"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
Возвращает текст, соответствующий текст `IScriptEntry` блок скрипта, блока функции или сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstr`  
 [out] Текст, который находится в теле одного из следующих:  
  
-   `IScriptEntry` Блок сценария  
  
-   `IScriptEntry` Функцией в блоке функция  
  
-   `IScriptEntry` Скриптлета обработчик событий  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)