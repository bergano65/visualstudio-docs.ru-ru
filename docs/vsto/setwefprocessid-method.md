---
title: Метод SetWefProcessId | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9dbd5a9ffb2ff9b3833dc8007fdfafb4b1a35857
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setwefprocessid-method"></a>Метод SetWefProcessId
  Представляет идентификатор процесса, который будет выполняться содержимого Framework расширения Web (WEF).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*dwProcessId*|Идентификатор процесса, который будет использоваться для запуска WEF содержимого.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## <a name="remarks"></a>Примечания  
 Этот метод должен вызываться после создания процесса WEF-содержимого, но перед запуском WEF содержимого.  
  
 Если необходимо присоединить отладчик к процессу содержимого WEF среды разработки среды необходимо выполнить эту операцию в реализации этого метода.  
  
  