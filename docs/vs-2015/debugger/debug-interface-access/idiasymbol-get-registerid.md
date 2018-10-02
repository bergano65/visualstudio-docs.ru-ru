---
title: IDiaSymbol::get_registerId | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_registerId method
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c56467426840fe9bd9cbb62c77b6f0889126647
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562203"
---
# <a name="idiasymbolgetregisterid"></a>IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaSymbol::get_registerId](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-registerid).  
  
Извлекает обозначение register расположения при [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) присваивается `LocIsEnregistered`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает обозначение register расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Если символ является относительно регистр, то есть если символа [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) присваивается `LocIsRegRel`, использовать `get_registerId` метод, а затем с помощью вызова [IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) метод для получения смещения из реестра, где находится символ.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)



