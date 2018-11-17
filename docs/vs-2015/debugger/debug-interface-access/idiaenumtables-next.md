---
title: IDiaEnumTables::Next | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaEnumTables::Next method
ms.assetid: 8d7bd359-d33e-4317-9674-d89283efd7de
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ebb9dc6c3e9cb6ade79c2109fbb267a7c2c22b05
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776529"
---
# <a name="idiaenumtablesnext"></a>IDiaEnumTables::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает указанное число таблиц в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next (   
   ULONG       celt,  
   IDiaTable** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество таблиц в перечислителе требуется получить.  
  
 `rgelt`  
 [out] Массив, который должен быть заполнен с помощью [IDiaTable](../../debugger/debug-interface-access/idiatable.md) объекты, представляющие нужные таблицы.  
  
 `pceltFetched`  
 [out] Возвращает количество таблиц в выбранных перечислитель.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если отсутствуют дополнительные таблицы. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)



