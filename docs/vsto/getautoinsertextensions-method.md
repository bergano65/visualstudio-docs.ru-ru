---
title: Метод GetAutoInsertExtensions
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9716f6adcee1d443e342074f3c46a57a1ace26db
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915894"
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
  
|Параметр|Описание:|  
|---------------|-----------------|  
|*psaExtensionNames*|Имена расширений приложений для Office.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## <a name="remarks"></a>Примечания  
 Каждое приложение для Office, вставляемый возвращается как имя расширения приложения Office, который соответствует значению в разделе **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. Узел должен искать эти значения в реестре и автоматически вставлять расширения.  
