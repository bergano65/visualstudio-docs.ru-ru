---
title: 'IDiaSymbol:: get_registerId | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 580637cf1058c8bfbd10ac7812e59c802830d95e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842980"
---
# <a name="idiasymbolget_registerid"></a>IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает обозначение регистра расположения, если [перечисление локатионтипе](../../debugger/debug-interface-access/locationtype.md) имеет значение `LocIsEnregistered` .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает обозначение регистра расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Remarks  
 Если символ является относительным по отношению к регистру, то есть если для [перечисления локатионтипе](../../debugger/debug-interface-access/locationtype.md) символа задано значение `LocIsRegRel` , используйте `get_registerId` метод, а затем вызов метода [IDiaSymbol:: get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) , чтобы получить смещение от регистра, в котором находится символ.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)
