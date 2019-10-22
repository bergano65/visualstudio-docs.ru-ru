---
title: 'Иактивескриптаусор:: Аддтипелиб | Документация Майкрософт'
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
ms.openlocfilehash: 5bd96732a905d3fc0732ccfeaf2b65ada82957f4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577229"
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
 окне CLSID (идентификатор класса) добавляемой библиотеки типов.  
  
 `dwMajor`  
 окне Основной номер версии.  
  
 `dwMinor`  
 окне Дополнительный номер версии.  
  
 `dwFlags`  
 окне Не используется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод вызывает `LoadTypeLib` для загрузки библиотеки типов. После успешного выполнения этот метод вызывает `IActiveScriptAuthor::AddNamedItem` для добавления сведений о типе.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иактивескриптаусор](../../winscript/reference/iactivescriptauthor-interface.md)  
 [Иактивескриптаусор:: AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)    
 [лоадтипелиб](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)