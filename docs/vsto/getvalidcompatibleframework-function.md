---
title: Функция GetValidCompatibleFramework
description: Узнайте, как API GetValidCompatibleFramework поддерживает инфраструктуру Office и не предназначен для непосредственного использования из кода.
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
ms.openlocfilehash: 96f536b3ab8e28b87a59a637fcf6dbaadeb21bf7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845080"
---
# <a name="getvalidcompatibleframework-function"></a>Функция GetValidCompatibleFramework
  Этот API поддерживает инфраструктуру Office и не предназначен для непосредственного использования в коде.

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
|*лпвсзкомпатиблефрамеворксксмл*|Не используйте.|
|*пбстрвалидфрамеворктаг*|Не используйте.|

## <a name="return-value"></a>Возвращаемое значение
 Если функция завершается с ошибкой, она возвращает **S_OK**. Если функция завершается ошибкой, возвращается код ошибки.
