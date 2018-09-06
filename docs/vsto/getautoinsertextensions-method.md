---
title: Метод GetAutoInsertExtensions
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
ms.openlocfilehash: 7e3e0fda420682e4f33c0d22a3e9c8caa920895b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674880"
---
# <a name="getautoinsertextensions-method"></a>Метод GetAutoInsertExtensions
  Получает сведения о приложениях для Office, который автоматически вставляются во время отладки.  
  
 Этот метод зарезервирован для использования в будущем.  
  
## <a name="syntax"></a>Синтаксис  
  
```csharp
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*psaExtensionNames*|Имена расширений приложений для Office.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## <a name="remarks"></a>Примечания  
 Каждое приложение для Office, вставляемый возвращается как имя расширения приложения Office, который соответствует значению в разделе **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Узел должен искать эти значения в реестре и автоматически вставлять расширения.  
  
  