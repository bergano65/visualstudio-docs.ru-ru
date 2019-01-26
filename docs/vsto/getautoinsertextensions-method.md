---
title: Метод GetAutoInsertExtensions
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
ms.openlocfilehash: debe61f07a8aa8711f1bb0b75ff0c2b39a528b21
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875840"
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
