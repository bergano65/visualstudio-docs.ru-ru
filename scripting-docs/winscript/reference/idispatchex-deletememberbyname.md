---
title: IDispatchEx::DeleteMemberByName | Документация Майкрософт
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
ms.openlocfilehash: dc7c8db4ab28e0bd0fcb48f352cb07595f72fd17
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000886"
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
 Имя элемента для удаления.  
  
 `grfdex`  
 Определяет, является ли имя члена с учетом регистра. Это может быть одно из следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|fdexNameCaseSensitive|Запросы, которые выполнить поиск имени регистра. Можно игнорировать объектом, который не поддерживает поиск с учетом регистра.|  
|fdexNameCaseInsensitive|Запросы, которые при поиске имени выполняться без учета регистра. Можно игнорировать объектом, который не поддерживает поиск без учета регистра.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`S_FALSE`|Элемент существует, но не может быть удален.|  
  
## <a name="remarks"></a>Примечания  
 Если элемент удаляется, идентификатор DISPID должен оставаться допустимым для `GetNextDispID`.  
  
 Если удаляется элемент с заданным именем и более поздней версии воссоздается член с тем же именем, идентификатор DISPID должны совпадать. (Члены, которые отличаются только регистром, совпадают ли «» зависит от объекта.)  
  
## <a name="example"></a>Пример  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)