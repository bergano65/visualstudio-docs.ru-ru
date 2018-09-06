---
title: Функция GetValidCompatibleFramework
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
ms.openlocfilehash: 18ef1d61d0e203744cc6436d884c37339a4a1ef0
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673875"
---
# <a name="getvalidcompatibleframework-function"></a>Функция GetValidCompatibleFramework
  Этот API поддерживает инфраструктуру Office и не предназначен для использования непосредственно из программного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Не следует использовать.|  
|*pbstrValidFrameworkTag*|Не следует использовать.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если функция завершается успешно, возвращается **S_OK**. Если функция завершается с ошибкой, возвращается код ошибки.  
  
  