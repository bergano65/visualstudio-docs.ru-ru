---
title: Функция EnsureVSTOComponent
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 20c4e363b11647609b67a898878dd4b4e59ba180
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/22/2018
---
# <a name="ensurevstocomponent-function"></a>Функция EnsureVSTOComponent
  Этот API поддерживает инфраструктуру Office и не предназначен для использования непосредственно из программного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```c  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*pProject*|Не следует использовать.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если функция выполняется успешно, он возвращает **S_OK**. Если функция завершается с ошибкой, возвращается код ошибки.  
  
  