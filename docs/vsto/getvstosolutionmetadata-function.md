---
title: Функция GetVstoSolutionMetadata
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
ms.openlocfilehash: d7714e78e897e6c8b391a6c30e9a548671ce80c4
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635011"
---
# <a name="getvstosolutionmetadata-function"></a>Функция GetVstoSolutionMetadata
  Этот API поддерживает инфраструктуру Office и не предназначен для использования непосредственно из программного кода.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание:|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|Не следует использовать.|
|*ppSolutionInfo*|Не следует использовать.|

## <a name="return-value"></a>Возвращаемое значение
 Если функция завершается успешно, возвращается **S_OK**. Если функция завершается с ошибкой, возвращается код ошибки.
