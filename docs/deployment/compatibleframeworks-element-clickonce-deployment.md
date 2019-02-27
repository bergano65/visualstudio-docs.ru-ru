---
title: '&lt;compatibleFrameworks&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d6fb1ab2addb58f9b28e1185fd55f9fdf63f5600
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628967"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; элемент (развертывание ClickOnce)
Идентифицирует версии платформы .NET Framework, где можно установить и выполнять это приложение.

> [!NOTE]
>  [*MageUI.exe* ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) не поддерживает `compatibleFrameworks` элемент при сохранении манифеста приложения, уже подписанного с помощью сертификата с помощью [ *MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Вместо этого средства используйте [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="syntax"></a>Синтаксис

```xml
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
 `compatibleFrameworks` Элемент является обязательным для манифестов развертывания, предназначенные [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] среды выполнения, предоставляемые [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] или более поздней версии. `compatibleFrameworks` Содержит один или несколько `framework` элементы, которые задают версий платформы .NET Framework, для которых можно запустить это приложение. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Среда выполнения будет запускаться приложение на первом доступных `framework` в этом списке.

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
 В следующем коде показано в примере `compatibleFrameworks` элемент [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания. Это развертывание может выполняться [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Оно также может выполняться [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] так как он является надмножеством [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>См. также
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)