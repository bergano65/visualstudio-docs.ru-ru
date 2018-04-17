---
title: Функция EnsureVSTOComponent | Документы Microsoft
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
ms.openlocfilehash: 5561d3c046c083c1495b858d36f6c867050ed842
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ensurevstocomponent-function"></a>Функция EnsureVSTOComponent
  Этот API поддерживает инфраструктуру Office и не предназначен для использования непосредственно из программного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
  
  