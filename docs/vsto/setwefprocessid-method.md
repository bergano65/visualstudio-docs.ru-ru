---
title: Метод SetWefProcessId
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
ms.openlocfilehash: 1352ccc9318061be4a2f9ad2da7d63715acd6721
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978360"
---
# <a name="setwefprocessid-method"></a>Метод SetWefProcessId
  Предоставляет идентификатор процесса, в которой выполняются расширения Framework Web (WEF) содержимое.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*dwProcessId*|Идентификатор процесса, который будет использоваться для запуска содержимого пересылки событий Windows.|

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Примечания
 Этот метод должен вызываться после создания содержимого процесс пересылки событий Windows, но прежде чем запускать любое содержимое пересылки событий Windows.

 Если вы хотите подключить отладчик к процессу содержимого пересылки событий Windows среды разработки, среды необходимо выполнить эту операцию в реализации этого метода.
