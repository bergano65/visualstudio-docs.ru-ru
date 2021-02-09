---
title: Метод SetWefProcessId
description: Узнайте, как метод SetWefProcessId предоставляет идентификатор процесса, который будет запускать содержимое платформы веб-расширений (WEF).
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
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882412"
---
# <a name="setwefprocessid-method"></a>Метод SetWefProcessId
  Предоставляет идентификатор процесса, который будет запускать содержимое платформы веб-расширений (WEF).

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*двпроцессид*|Идентификатор процесса, который будет использоваться для запуска содержимого WEF.|

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Remarks
 Этот метод должен вызываться после создания процесса содержимого WEF, но перед запуском содержимого WEF.

 Если требуется, чтобы среда разработки присоединит отладчик к процессу содержимого WEF, среда должна выполнить эту операцию в реализации этого метода.
