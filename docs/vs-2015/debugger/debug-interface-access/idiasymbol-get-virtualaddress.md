---
title: IDiaSymbol::get_virtualAddress | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualAddress method
ms.assetid: dc20c7c0-15a6-4b78-a5c9-2e0b94cac522
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6b7b1be1529374dbf4277ba75ca7b92267ef5d6
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64858019"
---
# <a name="idiasymbolgetvirtualaddress"></a>IDiaSymbol::get_virtualAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает виртуальный адрес (VA) расположения. Используется, когда [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) присваивается `LocIsStatic`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает виртуальный адрес расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)
