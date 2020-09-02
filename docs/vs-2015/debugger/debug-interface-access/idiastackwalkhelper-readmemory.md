---
title: 'Идиастакквалкхелпер:: readMemory | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bef01cd29bb2312bd682f2f1f1150ee78da293e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150056"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Считывает блок данных из образа исполняемого файла в памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `type`  
 окне Значение из перечисления [перечисления меморитипинум](../../debugger/debug-interface-access/memorytypeenum.md) , указывающее тип памяти для чтения.  
  
 va  
 окне Виртуальный адрес в образе, с которого начинается чтение.  
  
 `cbData`  
 окне Размер буфера данных в байтах.  
  
 `pcbData`  
 заполняет Возвращает число фактически считанных байтов. Если `pbData` параметр имеет значение `NULL` , то это общее число доступных байтов данных.  
  
 `pbData`  
 [вход, выход] Буфер, который заполняется считанной памятью.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиастакквалкхелпер](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)
