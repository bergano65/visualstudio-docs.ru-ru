---
title: IDiaSymbol::get_addressOffset | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressOffset method
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dfa54e09baa3cec238eb892599a8e1bd5910e17
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "64787015"
---
# <a name="idiasymbolgetaddressoffset"></a>IDiaSymbol::get_addressOffset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает часть смещения адрес расположения. Используется, когда [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) присваивается `LocIsStatic`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает часть смещения адрес расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Для статических элементов, расположенных в внешней библиотеке DLL смещение, возвращаемого этим методом может быть 0, так как этот метод использует получение виртуального адреса элемента. Виртуальные адреса допустимы только если [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) метод в [IDiaSession](../../debugger/debug-interface-access/idiasession.md) интерфейс был вызван с параметром ненулевое значение, указав адрес загрузки библиотеки DLL.  
  
 Чтобы получить раздел части адреса, вызовите [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) метод.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 7.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
