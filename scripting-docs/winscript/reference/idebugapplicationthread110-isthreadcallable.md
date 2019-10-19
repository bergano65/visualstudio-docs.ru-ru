---
title: 'IDebugApplicationThread110:: Иссреадкаллабле | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsThreadCallable
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ff81190247454a4471a4150843d3fb0aaed5999
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574464"
---
# <a name="idebugapplicationthread110isthreadcallable"></a>IDebugApplicationThread110::IsThreadCallable
Определяет, находится ли этот поток в состоянии, которое будет обрабатывать вызовы, выполненные с помощью механизмов переключения потоков PDM, таких как Синчронаускаллинсреад.  
  
> [!IMPORTANT]
> [Интерфейс IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) реализуется с помощью PDM v 11.0 и более поздних версий. Обнаружено в activdbg100.h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfIsCallable`  
 [out] `true`, если поток вызываемый; в противном случае `false`.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)