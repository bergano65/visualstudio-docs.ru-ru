---
title: Функция EnsureVSTOComponent
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
ms.openlocfilehash: cf55fc6669edd33d1b8896ee85f33ab2c04e844f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543589"
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
