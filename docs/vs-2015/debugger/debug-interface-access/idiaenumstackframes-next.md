---
title: 'Идиаенумстаккфрамес:: Next | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames::Next method
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c66e8b281f27e13a1176dd32f21856367e5f1ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189742"
---
# <a name="idiaenumstackframesnext"></a>IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает указанное число элементов кадра стека из последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 окне Число возвращаемых элементов StackFrame в перечислителе.  
  
 rgelt  
 заполняет Массив, который должен быть заполнен запрошенными объектами [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .  
  
 pceltFetched  
 заполняет Возвращает количество элементов кадра стека в выбранном перечислителе.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если больше нет кадров стека. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумстаккфрамес](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
