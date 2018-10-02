---
title: IDiaStackWalkFrame::readMemory | Документация Майкрософт
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
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e4bad4128ca89cf90ccf1c361bcc6de11d1d8f3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563513"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaStackWalkFrame::readMemory](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackwalkframe-readmemory).  
  
Читает содержимое памяти на основе образа.  
  
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
 [in] Один из [перечисление MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) значений перечисления, указывающее тип доступа к памяти.  
  
 `va`  
 [in] Виртуальный адрес расположения в образе должно начаться чтение.  
  
 `cbData`  
 [in] Размер буфера данных, в байтах.  
  
 `pcbData`  
 [out] Возвращает количество байтов, возвращаемых. Если `data` — `NULL`, затем `pcbData` содержит общее число байтов доступных данных.  
  
 `data`  
 [out] Буфер, который должен заполниться данными из указанного расположения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



