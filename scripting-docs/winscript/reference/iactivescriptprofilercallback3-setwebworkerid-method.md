---
title: Метод IActiveScriptProfilerCallback3::SetWebWorkerId | Документация Майкрософт
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
ms.openlocfilehash: f4025dbee7b8b5b246163a1919aec335a8863937
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347220"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>Метод IActiveScriptProfilerCallback3::SetWebWorkerId
Уведомляет профилировщик о ИД работника для этого сеанса профилирования. Если функция не выполняется в контексте страницы, этот метод не вызывается. Значение `webWorkerId` увеличивается на 1 для каждого исполнителя, начиная с 1. Значения Идентификаторов не предназначены для быть нестабильным за сеанс и соответствуют только в том порядке, в котором были созданы рабочие роли.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Параметры  
 `webWorkerId`  
 Идентификатор веб-рабочей роли.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода обрабатывается обработчиком сценариев.