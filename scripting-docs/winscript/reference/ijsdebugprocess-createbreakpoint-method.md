---
title: Метод IJsDebugProcess::CreateBreakPoint | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: b398b93c2e7b5ad43abd35d385407b39c0c980f9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152633"
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