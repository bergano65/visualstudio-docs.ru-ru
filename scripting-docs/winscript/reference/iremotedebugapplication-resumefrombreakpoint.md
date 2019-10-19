---
title: 'IRemoteDebugApplication:: Ресумефромбреакпоинт | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ResumeFromBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ResumeFromBreakPoint
ms.assetid: a613cc2b-1d69-4713-a235-64372c253b4a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fead9c14efbe73bd006a5ff3e1cfb10ad40404b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577462"
---
# <a name="iremotedebugapplicationresumefrombreakpoint"></a>IRemoteDebugApplication::ResumeFromBreakPoint
Возобновляет приложение, которое в данный момент находится в точке останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ResumeFromBreakPoint(  
   IRemoteDebugApplicationThread*  prptFocus,  
   BREAKRESUMEACTION               bra,  
   ERRORRESUMEACTION               era  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `prptFocus`  
 окне Для режимов пошагового режима — поток, на который влияет режим пошагового выполнения.  
  
 `bra`  
 окне Действие, выполняемое при возобновлении работы приложения.  
  
 `era`  
 окне Действие, выполняемое в случае, если приложение было остановлено из-за ошибки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод возобновляет приложение, которое в данный момент находится в точке останова.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)  
 @No__t_1 [перечисления BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)  
 [Перечисление ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)