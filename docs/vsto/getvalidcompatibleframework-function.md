---
title: Функция GetValidCompatibleFramework
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
ms.openlocfilehash: 79b97867a3a5c87f1e208d93efacea711ba71efc
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869311"
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
