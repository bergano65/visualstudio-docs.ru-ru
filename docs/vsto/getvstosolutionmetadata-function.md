---
title: Функция GetVstoSolutionMetadata
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aebbedaab7e7ac342f6d6ace191d820f6a0c8090
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520189"
---
# <a name="getvstosolutionmetadata-function"></a>Функция GetVstoSolutionMetadata
  Этот API поддерживает инфраструктуру Office и не предназначен для непосредственного использования в коде.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*лпвсзсолутионметадатакэй*|Не используйте.|
|*ппсолутионинфо*|Не используйте.|

## <a name="return-value"></a>Возвращаемое значение
 Если функция завершается с ошибкой, она возвращает **S_OK**. Если функция завершается ошибкой, возвращается код ошибки.
