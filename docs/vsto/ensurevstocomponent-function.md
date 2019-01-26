---
title: Функция EnsureVSTOComponent
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 912c28086bb918afa406fca7cf4acce06e5be099
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866088"
---
# <a name="ensurevstocomponent-function"></a>Функция EnsureVSTOComponent
  Этот API поддерживает инфраструктуру Office и не предназначен для использования непосредственно из программного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|*pProject*|Не следует использовать.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если функция завершается успешно, возвращается **S_OK**. Если функция завершается с ошибкой, возвращается код ошибки.  
