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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 523279d70215af90ea070ea8272a5221d9947582
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524327"
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
