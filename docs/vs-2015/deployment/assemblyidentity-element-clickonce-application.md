---
title: '&lt;&gt;элемент assemblyIdentity (приложение ClickOnce) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 5bde22809af69071f5484e25717a5aea7d78a603
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428538"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;&gt;элемент assemblyIdentity (приложение ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет приложение, развернутое в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывании.  
  
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
 `assemblyIdentity`Элемент является обязательным. Он не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательный. Определяет имя приложения.<br /><br /> Если `Name` содержит специальные символы, например одинарные или двойные кавычки, приложение может не выполнить активацию.|  
|`Version`|Обязательный. Указывает номер версии приложения в следующем формате: `major.minor.build.revision`|  
|`publicKeyToken`|Необязательный элемент. Задает 16-символьную шестнадцатеричную строку, представляющую последние 8 байт `SHA-1` хэш-значения открытого ключа, для которого подписано приложение или сборка. Открытый ключ, используемый для подписи каталога, должен иметь длину 2048 бит или больше.<br /><br /> Несмотря на то что подписывание сборки рекомендуется, но необязательно, этот атрибут является обязательным. Если сборка не подписана, следует скопировать значение из самозаверяющего сборки или использовать фиктивные значения всех нулей.|  
|`processorArchitecture`|Обязательный. Указывает процессор. Допустимые значения: `msil` для всех процессоров, `x86` для 32-разрядных ОС Windows, `IA64` для 64-разрядной версии Windows и `Itanium` для процессоров Intel 64-bit Itanium.|  
|`language`|Обязательный. Определяет коды языка двух частей (например, `en-US` ) сборки. Этот элемент находится в `asmv2` пространстве имен. Если значение не указано, по умолчанию используется значение `neutral` .|  
  
## <a name="examples"></a>Примеры  
  
### <a name="description"></a>Описание  
 В следующем примере кода показан `assemblyIdentity` элемент в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесте приложения. Этот пример кода является частью большого примера, приведенного в [манифесте приложения ClickOnce](../deployment/clickonce-application-manifest.md).  
  
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
  
## <a name="see-also"></a>См. также:  
 [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity> Элемент](../deployment/assemblyidentity-element-clickonce-deployment.md)
