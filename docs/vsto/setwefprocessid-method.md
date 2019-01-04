---
title: Метод SetWefProcessId
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3ccce49992073f11245929bf7af0b966537bd079
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53886154"
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
