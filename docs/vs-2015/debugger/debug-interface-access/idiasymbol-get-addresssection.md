---
title: IDiaSymbol::get_addressSection | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_addressSection method
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cff7d51b1e07c26b9c5d88ce81301f4ca8c50d93
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978504"
---
# <a name="idiasymbolgetaddresssection"></a>IDiaSymbol::get_addressSection
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает раздел часть опции адрес. Используется, когда [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) присваивается `LocIsStatic`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает часть раздела опции адрес.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Для статических элементов, расположенных в внешней библиотеке DLL раздел, возвращаемого этим методом может быть 0, так как этот метод использует получение виртуального адреса элемента. Виртуальные адреса допустимы только если [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) метод в [IDiaSession](../../debugger/debug-interface-access/idiasession.md) интерфейс был вызван с параметром ненулевое значение, указав адрес загрузки библиотеки DLL.  
  
 Чтобы получить часть смещения адреса, вызовите [IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) метод.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 7.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)
