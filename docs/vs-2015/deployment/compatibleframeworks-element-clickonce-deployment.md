---
title: '&lt;&gt;элемент compatibleFrameworks (развертывание ClickOnce) | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675413"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;&gt;элемент compatibleFrameworks (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Идентифицирует версии платформы .NET Framework, где можно установить и выполнять это приложение.  
  
> [!NOTE]
> [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) не поддерживает `compatibleFrameworks` элемент при сохранении манифеста приложения, который уже подписан с помощью сертификата, использующего [MageUI.exe](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Вместо этого средства используйте [Mage.exe](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
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
 `compatibleFrameworks`Элемент необходим для манифестов развертывания, предназначенных для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] среды выполнения, предоставляемой [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] или более поздней версии. `compatibleFrameworks`Элемент содержит один или несколько `framework` элементов, указывающих версии .NET Framework, в которых может выполняться это приложение. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Среда выполнения запустит приложение в первом доступном `framework` списке.  
  
 В следующей таблице перечислены атрибуты, `compatibleFrameworks` поддерживаемые элементом.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`S` `upportUrl`|Необязательный элемент. Указывает URL-адрес, по которому может быть скачана предпочтительная совместимая версия .NET Framework.|  
  
## <a name="framework"></a>платформа  
 Обязательный. В следующей таблице перечислены атрибуты, которые `framework` поддерживает элемент.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`targetVersion`|Обязательный. Указывает номер версии целевого .NET Framework.|  
|`profile`|Обязательный. Указывает профиль целевого .NET Framework.|  
|`supportedRuntime`|Обязательный. Указывает номер версии среды выполнения, связанной с целевым .NET Framework.|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `compatibleFrameworks` элемент в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесте развертывания. Это развертывание может выполняться на [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] . Он также может выполняться в, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] так как является надмножеством [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>См. также:  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
