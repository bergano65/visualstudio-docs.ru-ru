---
title: "IDispatchEx::DeleteMemberByName | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Удаляет элемент по имени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `bstrName`  
 Имя элемента для удаления.  
  
 `grfdex`  
 Определяет, является ли регистр имени члена. Это может быть одно из следующих значений:  
  
|Значение|Значение|  
|-----------|-------------|  
|fdexNameCaseSensitive|Запросы, которые выполнить поиск имени регистра. Можно игнорировать объектом, который не поддерживает поиск с учетом регистра.|  
|fdexNameCaseInsensitive|Запросы, которые выполнить поиск имени регистра. Можно игнорировать объектом, который не поддерживает поиск без учета регистра.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|||  
|-|-|  
|`S_OK`|Выполнено.|  
|`S_FALSE`|Элемент существует, но не может быть удалена.|  
  
## <a name="remarks"></a>Примечания  
 При удалении члена DISPID должен оставаться действительным для `GetNextDispID`.  
  
 Если удаляется элемент с заданным именем и в дальнейшем воссоздать член с тем же именем, идентификатор DISPID должны совпадать. (Члены, которые различаются только регистром одинаковы ли «» зависит от объекта.)  
  
## <a name="example"></a>Пример  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)