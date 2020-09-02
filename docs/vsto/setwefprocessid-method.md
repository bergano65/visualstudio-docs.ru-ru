---
title: Метод SetWefProcessId
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
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537336"
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
