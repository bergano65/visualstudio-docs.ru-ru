---
title: "IDiaAddressMap::put_addressMapEnabled | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5542e00511301a84ba54a08405434001f63c4b5d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Указывает, следует ли использовать для преобразования символа адресов Карта адресов.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 NewVal  
 [in] Значение `TRUE` Включение трансляции символов, или `FALSE` для отключения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Иногда исполняемый процессоров после обновления исполняемый файл. ПАКЕТ содержит механизм для поддержки преобразования символов в новый макет.  
  
 При загрузке PDB-файл включен адрес карты, хранящихся в файле. Бывают случаи, тем не менее, когда клиентское приложение может понадобиться предоставить свой собственный адрес карты путем вызова [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) метод. Если `set_addressMap` метод завершается успешно, клиентское приложение должно вызывать `put_addressMapEnabled` метод с `NewVal` параметр `TRUE` Чтобы использовать этот адрес карты.  
  
 Текущее состояние включаемой карты адрес можно получить с помощью вызова [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)