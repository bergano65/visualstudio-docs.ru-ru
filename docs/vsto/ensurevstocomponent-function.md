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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a04cfc249efa4640df2b2e4b1c5f4b43ed52ace2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846120"
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
