---
title: '&lt;Описание&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c926da377688b1248daa01f015cda7914434a36
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55013903"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Описание&gt; элемент (развертывание ClickOnce)
Идентифицирует сведения о приложении, используемый для создания оболочки присутствия и **Установка и удаление программ** панели управления.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
      <description   
   publisher   
   product  
   suiteName  
   supportUrl  
/>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `description` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v1` . Он не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`publisher`|Обязательный. Идентифицирует имя компании, используемое для размещения значка в Windows **запустить** меню и **Установка и удаление программ** панели управления, если развертывание настроено для установки.|  
|`product`|Обязательный. Определяет полное название продукта. Используется в качестве названия значка, установленного в Windows **запустить** меню.|  
|`suiteName`|Необязательный параметр. Указывает вложенную `publisher` папки в Windows **запустить** меню.|  
|`supportUrl`|Необязательный параметр. Указывает URL-адрес поддержки, которое отображается в **Установка и удаление программ** панели управления. Ярлык на этот URL-адрес также создается для поддержки приложения в Windows **запустить** меню, когда развертывание настроено для установки.|  
  
## <a name="remarks"></a>Примечания  
 Элемент "description" необходим во всех конфигурациях развертывания.  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано `description` элемент [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифест развертывания. Данный пример кода является частью большего примера для [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) раздела.  
  
```xml  
<description   
  asmv2:publisher="My Company Name"  
  asmv2:product="My Application"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>См. также  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)