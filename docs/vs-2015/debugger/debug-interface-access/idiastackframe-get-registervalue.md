---
title: IDiaStackFrame::get_registerValue | Документация Майкрософт
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
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 340291d7dfa36c45b92f49f383cbacb0e234b7f4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200789"
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает значение указанного регистра, как хранящиеся в кадре стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `registerIndex`  
 [in] Один из [перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) значений перечисления.  
  
 `pRetVal`  
 [out] Значение, хранящееся в регистре.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)



