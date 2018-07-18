---
title: Метод IJsDebugFrame::GetStackRange | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727874"
---
# <a name="ijsdebugframegetstackrange-method"></a>Метод IJsDebugFrame::GetStackRange
Возвращает диапазон абсолютных адресов кадра стека логических JavaScript.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pStart`  
 [out] Нижняя большинство указатель стека для фрейма.  
  
 `pEnd`  
 [out] Первые большинство устройство для раскладки указатель кадра.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="remarks"></a>Примечания  
 Этот метод полезен для комбинирования трассировок стека с чередованием, собранных из нескольких сред выполнения. Начало, конец указатели стека может охватывать несколько кадров стека физического компьютера (для интерпретируемых кадров среды выполнения JavaScript). Пуск > Завершить при увеличении стека от высокой низкий адрес.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)