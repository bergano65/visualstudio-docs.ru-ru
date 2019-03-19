---
title: IActiveScriptAuthor::AddTypeLib | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5967438c620a89df98c74c8824809b8fdaf739a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153636"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
Добавляет библиотеку типов в пространство имен для скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rguidTypeLib`  
 [in] CLSID (идентификатор класса) библиотеки типов для добавления.  
  
 `dwMajor`  
 [in] Основной номер версии.  
  
 `dwMinor`  
 [in] Дополнительный номер версии.  
  
 `dwFlags`  
 [in] Не используется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывает метод `LoadTypeLib` для загрузки библиотеки типов. В случае успеха этот метод вызывает `IActiveScriptAuthor::AddNamedItem` для добавления сведений о типе.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)