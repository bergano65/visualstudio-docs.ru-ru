---
title: Метод GetAutoInsertExtensions | Документы Microsoft
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
ms.openlocfilehash: 67f6bfcb0ee38acf9abb604f28fa95eeaa605fde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getautoinsertextensions-method"></a>Метод GetAutoInsertExtensions
  Возвращает сведения о приложениях для Office, которые вставляются автоматически во время отладки.  
  
 Этот метод зарезервирован для использования в будущем.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetAutoInsertExtensions(  
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames  
);  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*psaExtensionNames*|Чтобы имена расширений приложений для Office.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## <a name="remarks"></a>Примечания  
 Каждое приложение для Office для вставки возвращается как имя расширения приложений Office, которой соответствует значению в разделе HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer. Узел должен искать эти значения в реестре и автоматически вставлять расширения.  
  
  