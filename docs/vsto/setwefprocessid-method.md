---
title: "Метод SetWefProcessId | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dd4abab178c951c6150653a1228c2077c5585808
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
|Параметр|Описание:|  
|---------------|-----------------|  
|*dwProcessId*|Идентификатор процесса, который будет использоваться для запуска WEF содержимого.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## <a name="remarks"></a>Примечания  
 Этот метод должен вызываться после создания процесса WEF-содержимого, но перед запуском WEF содержимого.  
  
 Если необходимо присоединить отладчик к процессу содержимого WEF среды разработки среды необходимо выполнить эту операцию в реализации этого метода.  
  
  