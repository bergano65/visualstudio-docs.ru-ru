---
title: IDiaStackWalkHelper::imageForVA | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26cb6957edd30d36fbc1a9ebbf982fd3ce91c94a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971251"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Возвращает дату начала исполняемый образ в памяти, выделяемый виртуальный адрес где-то в область памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `vaContext`  
 [in] Виртуальный адрес, который лежит где-то в пространстве исполняемый файл.  
  
 `pvaImageStart`  
 [out] Возвращает начальный виртуальный адрес исполняемого образа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)