---
title: Метод IActiveScriptProfilerCallback3::SetWebWorkerId | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0798a23b4c8ad4e5859bec73ebfed47a56b322d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993107"
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