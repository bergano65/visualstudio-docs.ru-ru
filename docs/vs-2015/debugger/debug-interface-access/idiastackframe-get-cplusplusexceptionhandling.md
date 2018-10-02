---
title: IDiaStackFrame::get_cplusplusExceptionHandling | Документация Майкрософт
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
- IDiaStackFrame::get_cplusplusExceptionHandling method
ms.assetid: f2631820-c986-40ca-b61e-230d7a9c426c
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55fbcb7d6a50e4021c070c2fd6971d21f1f767e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571404"
---
# <a name="idiastackframegetcplusplusexceptionhandling"></a>IDiaStackFrame::get_cplusplusExceptionHandling
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaStackFrame::get_cplusplusExceptionHandling](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling).  
  
Получает флаг, указывающий, если обработка исключений с ++ действует.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_cplusplusExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `TRUE` Если обработка исключений с ++ действует для этого фрейма; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Обработка исключений C++ не так же, как структурированный или система обработки исключений.  
  
 Чтобы определить, если структурированной обработки исключений действует, вызовите [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)



