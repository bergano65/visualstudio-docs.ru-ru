---
title: "IActiveScriptAuthor::RemoveTypeLib | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveTypeLib
ms.assetid: 232c3698-024d-4549-8fbc-cb0d3ac17dc5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91d44d2f910a1523d0c45871e01d0258dcdd4138
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorremovetypelib"></a>IActiveScriptAuthor::RemoveTypeLib
Удаляет библиотеку типов из скрипта создания engine пространства имен.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT RemoveTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rguidTypeLib`  
 [in] Код CLSID (идентификатор класса) библиотеки типов для удаления.  
  
 `dwMajor`  
 [in] Основной номер версии.  
  
 `dwMinor`  
 [in] Дополнительный номер версии.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)