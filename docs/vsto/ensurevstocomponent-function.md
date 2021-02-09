---
title: Функция EnsureVSTOComponent
description: Узнайте, как API EnsureVSTOComponent поддерживает инфраструктуру Office и не предназначен для непосредственного использования из кода.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 17f52a469d93a843ef776c125e15a37db22277e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910472"
---
# <a name="ensurevstocomponent-function"></a>Функция EnsureVSTOComponent
  Этот API поддерживает инфраструктуру Office и не предназначен для непосредственного использования в коде.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT EnsureVSTOComponent(
    IVSTProject *pProject
);
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*ппрожект*|Не используйте.|

## <a name="return-value"></a>Возвращаемое значение
 Если функция завершается с ошибкой, она возвращает **S_OK**. Если функция завершается ошибкой, возвращается код ошибки.
