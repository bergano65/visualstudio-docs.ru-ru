---
title: IActiveScriptAuthor::RemoveTypeLib | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveTypeLib
ms.assetid: 232c3698-024d-4549-8fbc-cb0d3ac17dc5
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8dd75bfa5474eb93a51af790f7efd6431a9aaa0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149186"
---
# <a name="iactivescriptauthorremovetypelib"></a>IActiveScriptAuthor::RemoveTypeLib
Удаляет библиотеку типов из скрипта создания пространства имен модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT RemoveTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rguidTypeLib`  
 [in] CLSID (идентификатор класса) библиотеки типов для удаления.  
  
 `dwMajor`  
 [in] Основной номер версии.  
  
 `dwMinor`  
 [in] Дополнительный номер версии.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)