---
title: Метод IActiveScriptProfilerCallback3::SetWebWorkerId | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 426767b8d4d23964d6bfaa7102ee53b550e7ab9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724614"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>Метод IActiveScriptProfilerCallback3::SetWebWorkerId
Уведомляет профилировщик о идентификатор работника для этого сеанса профилирования. Если функция не выполняется в контексте страницы, этот метод не вызывается. Значение `webWorkerId` увеличивается на 1 для каждого исполнителя, начиная с 1. Значения Идентификаторов не предназначены для быть нестабильным после завершения сеанса и относятся только к порядок, в котором были созданы работников.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Параметры  
 `webWorkerId`  
 Идентификатор работника web  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода обрабатывается обработчиком сценариев.