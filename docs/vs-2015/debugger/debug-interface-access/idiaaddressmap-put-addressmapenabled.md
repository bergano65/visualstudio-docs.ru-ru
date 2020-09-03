---
title: IDiaAddressMap::p ut_addressMapEnabled | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198673"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает, следует ли использовать карту адресов для преобразования адресов символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 неввал  
 окне Задайте для значение `TRUE` , чтобы разрешить перевод символов или `FALSE` Отключить.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Исполняемые процедуры, выполняемые после выполнения обработчиков, иногда обновляют исполняемый файл. DIA содержит механизм для поддержки перевода символов в новый макет.  
  
 При загрузке PDB-файла таблица адресов, хранимая в файле, становится доступной. Однако бывают случаи, когда клиентскому приложению может потребоваться предоставить собственную карту адресов, вызвав метод [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) . Если `set_addressMap` метод выполнен успешно, клиентское приложение должно вызвать `put_addressMapEnabled` метод с `NewVal` параметром, `TRUE` чтобы разрешить использование этой схемы адресов.  
  
 Текущее состояние включенной таблицы адресов можно получить с помощью вызова метода [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
