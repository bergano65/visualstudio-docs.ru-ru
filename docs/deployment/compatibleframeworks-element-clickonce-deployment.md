---
title: '&lt;compatibleFrameworks&gt; элемент (развертывание ClickOnce) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d406ecf058bf1c570b57ed8f50815cc3d9378cbe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; элемент (развертывание ClickOnce)
Идентифицирует версии платформы .NET Framework, где можно установить и выполнять это приложение.  
  
> [!NOTE]
>  [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) не поддерживает `compatibleFrameworks` элемент при сохранении манифеста приложения, которое уже было подписано сертификат с помощью [MageUI.exe](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Вместо этого средства используйте [Mage.exe](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
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
 `compatibleFrameworks` Элемент является обязательным для манифестов развертывания, целевыми [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] среды выполнения, предоставляемых [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] или более поздней версии. `compatibleFrameworks` Элемент содержит один или несколько `framework` элементы, которые задают версий .NET Framework, на которых можно запустить это приложение. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Среда выполнения будет запускаться приложение на первой доступной `framework` в этом списке.  
  
 В следующей таблице перечислены атрибут, `compatibleFrameworks` поддерживает элемент.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`S` `upportUrl`|Необязательный. Указывает URL-адрес, где можно скачать предпочтительные совместимую версию .NET Framework.|  
  
## <a name="framework"></a>платформа  
 Обязательно. В следующей таблице перечислены атрибуты, `framework` поддерживает элемент.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`targetVersion`|Обязательно. Указывает номер версии платформы .NET Framework.|  
|`profile`|Обязательно. Задает профиль платформы .NET Framework.|  
|`supportedRuntime`|Обязательно. Указывает номер версии среды выполнения, связанной с платформы .NET Framework.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В следующем примере кода показан `compatibleFrameworks` элемент в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания. Может выполняться это развертывание [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Также можно запустить на [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , так как он является надмножеством [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
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