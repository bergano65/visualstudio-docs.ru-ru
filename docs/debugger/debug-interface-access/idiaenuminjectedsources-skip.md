---
title: IDiaEnumInjectedSources::Skip | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Skip method
ms.assetid: 4aad6a51-f2d3-4064-b216-60d830d0a560
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c08266ab4307b382acc5cff3210744a97e79fc02
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55023487"
---
# <a name="idiaenuminjectedsourcesskip"></a>IDiaEnumInjectedSources::Skip
Пропускает заданное число источников, внедренного в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 celt  
 [in] Число источников, внедренного в последовательности перечисления, чтобы пропустить.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` Если существует больше нет внедренного источника для пропуска.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)