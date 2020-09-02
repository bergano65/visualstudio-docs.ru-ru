---
title: 'Идиастакквалкфраме:: readMemory | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97a868973d2a514150b8d728e685523e918f88f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150167"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Считывает память из образа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `type`  
 окне Одно из значений перечисления [перечисления меморитипинум](../../debugger/debug-interface-access/memorytypeenum.md) , указывающее тип памяти для доступа.  
  
 `va`  
 окне Расположение виртуального адреса в образе для начала чтения.  
  
 `cbData`  
 окне Размер буфера данных в байтах.  
  
 `pcbData`  
 заполняет Возвращает число возвращенных байтов. Если `data` параметр имеет значение `NULL` , то `pcbData` содержит общее число доступных байтов данных.  
  
 `data`  
 заполняет Буфер, который должен быть заполнен данными из указанного расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
