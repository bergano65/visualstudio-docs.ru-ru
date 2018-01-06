---
title: "Метод GetAutoInsertExtensions | Документы Microsoft"
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
ms.assetid: 78388cce-7aae-4163-8db5-ce00d0a0c331
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cef8de366b812baee96ba889cc26157594d55954
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
|Параметр|Описание:|  
|---------------|-----------------|  
|*psaExtensionNames*|Чтобы имена расширений приложений для Office.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## <a name="remarks"></a>Примечания  
 Каждое приложение для Office для вставки возвращается как имя расширения приложений Office, которой соответствует значению в разделе HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer. Узел должен искать эти значения в реестре и автоматически вставлять расширения.  
  
  