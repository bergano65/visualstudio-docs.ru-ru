---
title: '&lt;assemblyIdentity&gt; элемент (приложение ClickOnce) | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 67ee803e18a1b098cd8e1bad2befd5a2d794766c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573049"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity&gt; элемент (приложение ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [ &lt;assemblyIdentity&gt; элемент (приложение ClickOnce)](https://docs.microsoft.com/visualstudio/deployment/assemblyidentity-element-clickonce-application).  
  
Идентифицирует приложение, развернутое в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `assemblyIdentity` Элемент является обязательным. Он не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательно. Определяет имя приложения.<br /><br /> Если `Name` содержит специальные символы, такие как одинарные или двойные кавычки, приложение может вызвать сбой активации.|  
|`Version`|Обязательно. Указывает номер версии приложения в следующем формате: `major.minor.build.revision`|  
|`publicKeyToken`|Необязательный. Указывает, 16-знаковая шестнадцатеричную строку, которая представляет собой последние 8 байт `SHA-1` хэш-значение открытого ключа, которым подписаны приложение или сборка. Открытый ключ, используемый для подписи каталога должен быть 2048 бит или более поздней версии.<br /><br /> Несмотря на то, что подпись сборки, рекомендуется, но необязательно, этот атрибут является обязательным. Если сборка не подписана, следует скопировать значение из собственной подписью сборки или использовать значение «пустого» все нули.|  
|`processorArchitecture`|Обязательно. Указывает процессор. Допустимые значения: `msil` для всех процессоров `x86` для 32-разрядной Windows, `IA64` для 64-разрядной Windows, и `Itanium` для Intel 64-разрядных процессоров Itanium.|  
|`language`|Обязательно. Определяет две части кодов языка (например, `en-US`) сборки. Этот элемент имеет `asmv2` пространства имен. Если этот атрибут не задан, по умолчанию используется `neutral`.|  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 В следующем примере кода показано `assemblyIdentity` элемент [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифест приложения. Данный пример кода является частью большего примера, приведенного в [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
### <a name="code"></a>Код  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity > элемент](../deployment/assemblyidentity-element-clickonce-deployment.md)



