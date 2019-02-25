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
ms.openlocfilehash: b975a4b4b2c1b4ae3f6ef0f1d6d23769bb4c77c7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56643513"
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

|Параметр|Описание:|
|---------------|-----------------|
|*lpwszCompatibleFrameworksXML*|Не следует использовать.|
|*pbstrValidFrameworkTag*|Не следует использовать.|

## <a name="return-value"></a>Возвращаемое значение
 Если функция завершается успешно, возвращается **S_OK**. Если функция завершается с ошибкой, возвращается код ошибки.
