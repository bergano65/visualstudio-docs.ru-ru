---
title: '&lt;compatibleFrameworks&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ef54062bd74c9395e187503dd12db1c0cd70d822
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675413"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; элемент (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Идентифицирует версии платформы .NET Framework, где можно установить и выполнять это приложение.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) не поддерживает `compatibleFrameworks` элемент при сохранении манифеста приложения, уже подписанного с помощью сертификата с помощью [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Вместо этого средства используйте [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `compatibleFrameworks` Элемент является обязательным для манифестов развертывания, предназначенные [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] среды выполнения, предоставляемые [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] или более поздней версии. `compatibleFrameworks` Содержит один или несколько `framework` элементы, которые задают версий платформы .NET Framework, для которых можно запустить это приложение. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Среда выполнения будет запускаться приложение на первом доступных `framework` в этом списке.  
  
 В следующей таблице перечислены атрибут, `compatibleFrameworks` поддерживает элемент.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`S` `upportUrl`|Необязательный параметр. Указывает URL-адрес, где можно скачать предпочтительные совместимой версии .NET Framework.|  
  
## <a name="framework"></a>платформа  
 Обязательный. В следующей таблице перечислены атрибуты, `framework` поддерживает элемент.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`targetVersion`|Обязательный. Указывает номер версии целевой платформы .NET Framework.|  
|`profile`|Обязательный. Задает профиль целевой платформы .NET Framework.|  
|`supportedRuntime`|Обязательный. Указывает номер версии среды выполнения, связанной с платформы .NET Framework.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В следующем коде показано в примере `compatibleFrameworks` элемент [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест развертывания. Это развертывание может выполняться [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)]. Оно также может выполняться [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] так как он является надмножеством [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
