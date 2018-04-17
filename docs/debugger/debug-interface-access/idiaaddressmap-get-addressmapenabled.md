---
title: IDiaAddressMap::get_addressMapEnabled | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 225cac39cb56bbf5b03478c6009162c711baad87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Указывает, установлен ли Карта адресов для конкретного сеанса.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pRetVal  
 [out] Возвращает `TRUE` Если включено сопоставление адресов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Иногда исполняемый процессоров после обновления исполняемый файл. ПАКЕТ содержит механизм для поддержки преобразования символов в новый макет.  
  
 Клиентские приложения можно задать адрес карты для конкретного сеанса, обратившись [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) интерфейс из [IDiaSession](../../debugger/debug-interface-access/idiasession.md) интерфейс и вызывая метод [IDiaAddressMap::set_ addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод после вызова, чтобы [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) метод. `get_addressMapEnabled` Метод возвращает результат вызова метода `put_addressMapEnabled` метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)