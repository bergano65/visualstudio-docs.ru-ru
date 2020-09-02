---
title: 'Идиатабле:: get_Count | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::get_Count method
ms.assetid: bb47abe8-6706-4679-bc52-79f6444dae7e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2332293e144cca74d7532e5ae5b1a14ca469adf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157531"
---
# <a name="idiatableget_count"></a>IDiaTable::get_Count
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает количество элементов в таблице.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает число элементов в таблице.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиатабле](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)
