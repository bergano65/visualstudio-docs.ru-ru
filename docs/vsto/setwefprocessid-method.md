---
title: Метод SetWefProcessId
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
ms.openlocfilehash: b426237816bfee53e7c3e50c19e29168b27e16e1
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693436"
---
# <a name="setwefprocessid-method"></a>Метод SetWefProcessId
  Представляет идентификатор процесса, который будет выполняться содержимого Framework расширения Web (WEF).  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|*dwProcessId*|Идентификатор процесса, который будет использоваться для запуска WEF содержимого.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## <a name="remarks"></a>Примечания  
 Этот метод должен вызываться после создания процесса WEF-содержимого, но перед запуском WEF содержимого.  
  
 Если необходимо присоединить отладчик к процессу содержимого WEF среды разработки среды необходимо выполнить эту операцию в реализации этого метода.  
  
  