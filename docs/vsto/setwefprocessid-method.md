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
ms.openlocfilehash: 7807d0495c5f0548178b1bc2ecae12d57cc3b072
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876126"
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
