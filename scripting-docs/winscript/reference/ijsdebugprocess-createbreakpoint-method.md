---
title: Метод IJsDebugProcess::CreateBreakPoint | Документы Microsoft
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
ms.openlocfilehash: 10d734f32d092d341dbb1b02a5cc7a0c127223a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728124"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>Метод IJsDebugProcess::CreateBreakPoint
Задает точку останова в позиции указанного документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Длина текста документа, в которой следует вставить точку останова.  
  
 `isEnabled`  
 [in] Указывает, включена ли точка останова.  
  
 `ppDebugBreakPoint`  
 [out] Объект, представляющий точку останова, в которой был создан.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)