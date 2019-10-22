---
title: IDispatchEx::D Елетемембербинаме | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576612"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Удаляет элемент по имени.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `bstrName`  
 Имя удаляемого элемента.  
  
 `grfdex`  
 Определяет, учитывается ли в имени члена регистр. Это может быть одно из следующих значений:  
  
|значения|Смысл|  
|-----------|-------------|  
|фдекснамекасесенситиве|Запрашивает, что поиск имени выполняется с учетом регистра. Может игнорироваться объектом, который не поддерживает поиск с учетом регистра.|  
|фдекснамекасеинсенситиве|Запрашивает, что поиск имени выполняется без учета регистра. Может игнорироваться объектом, который не поддерживает поиск без учета регистра.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`S_FALSE`|Элемент существует, но не может быть удален.|  
  
## <a name="remarks"></a>Заметки  
 Если элемент удален, идентификатор DISPID должен оставаться допустимым для `GetNextDispID`.  
  
 Если элемент с заданным именем удаляется, а позднее элемент с таким же именем создается повторно, идентификатор DISPID должен быть таким же. (Независимо от того, являются ли члены, отличающиеся только регистром,, зависит от объекта.)  
  
## <a name="example"></a>Пример  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)