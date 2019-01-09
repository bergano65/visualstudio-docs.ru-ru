---
title: IDispatchEx::GetNameSpaceParent | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 142248d4cfedb2d63025fc873c5574c163fcafd4
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087507"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
Извлекает интерфейс для пространства имен родительского объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppunk`  
 Адрес `IUnknown` указатель интерфейса, получающий интерфейс пространства имен родительского элемента.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` успеха или код ошибки, определенное OLE, в противном случае.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)