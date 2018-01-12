---
title: "Функция GetValidCompatibleFramework | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 43056033f6d23eb385609ebaf4d448ebdb2424a8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="getvalidcompatibleframework-function"></a>Функция GetValidCompatibleFramework
  Этот API поддерживает инфраструктуру Office и не предназначен для использования непосредственно из программного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Не следует использовать.|  
|*pbstrValidFrameworkTag*|Не следует использовать.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если функция выполняется успешно, он возвращает **S_OK**. Если функция завершается с ошибкой, возвращается код ошибки.  
  
  