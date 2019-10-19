---
title: 'Метод метод ijsdebugprocess:: CreateBreakPoint | Документация Майкрософт'
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
ms.openlocfilehash: 2b0a4d595a11dc54829c467a0aace9601042fa08
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575092"
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>Метод IJsDebugProcess::CreateBreakPoint
Задает точку останова в указанной позиции документа.  
  
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
 окне Указатель на Идебугдокументтекст.  
  
 `characterOffset`  
 окне Смещение символа от начала файла.  
  
 `characterCount`  
 окне Длина текста документа, в который должна быть вставлена Точка останова.  
  
 `isEnabled`  
 окне Указывает, включена ли точка останова.  
  
 `ppDebugBreakPoint`  
 заполняет Объект, представляющий созданную точку останова.  
  
## <a name="return-value"></a>Возвращаемое значение  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)