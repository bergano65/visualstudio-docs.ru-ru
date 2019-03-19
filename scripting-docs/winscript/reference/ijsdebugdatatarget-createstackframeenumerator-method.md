---
title: Метод IJsDebugDataTarget::CreateStackFrameEnumerator | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.CreateStackFrameEnumerator
apilocation:
- jscript9diag.dll
ms.assetid: cda172e5-18d0-43c5-81d8-432ab30ee70d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b8103ac689ac812aee2037f0f2e89f1d3a7448c6
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155430"
---
# <a name="ijsdebugdatatargetcreatestackframeenumerator-method"></a>Метод IJsDebugDataTarget::CreateStackFrameEnumerator
Создает перечислитель для кадров стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CreateStackFrameEnumerator(  
   DWORD threadId,  
   IEnumJsStackFrames **ppEnumerator  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `threadId`  
 [in] Поток, выполняемый в целевом процессе.  
  
 `ppEnumerator`  
 [out] Перечислитель для кадров стека.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)