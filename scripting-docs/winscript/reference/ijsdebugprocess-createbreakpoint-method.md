---
title: Метод IJsDebugProcess::CreateBreakPoint | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProcess.CreateBreakPoint
apilocation:
- jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 661e584133f4ec3c4e571d157a63844c5b1145b7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097569"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>Метод IJsDebugProcess::CreateBreakPoint
Задает точку останова в позицию указанного документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `documentId`  
 [in] Указатель на IDebugDocumentText.  
  
 `characterOffset`  
 [in] Символ смещение от начала файла.  
  
 `characterCount`  
 [in] Длина текста документа, в течение которого следует вставить точку останова.  
  
 `isEnabled`  
 [in] Указывает, включена ли точка останова.  
  
 `ppDebugBreakPoint`  
 [out] Объект, представляющий точку останова, которая была создана.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)