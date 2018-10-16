---
title: '&lt;Описание&gt; элемент (развертывание ClickOnce) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b8985bc83299f55cec3c5f41fd3d76c8801fdf34
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079814"
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
 Элемент `description` обязателен и находится в пространстве имен `urn:schemas-microsoft-com:asm.v1`. Он не содержит дочерних элементов и имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`publisher`|Обязательно. Идентифицирует имя компании, используемое для размещения значка в Windows **запустить** меню и **Установка и удаление программ** панели управления, если развертывание настроено для установки.|  
|`product`|Обязательно. Определяет полное название продукта. Используется в качестве названия значка, установленного в Windows **запустить** меню.|  
|`suiteName`|Необязательный. Указывает вложенную `publisher` папки в Windows **запустить** меню.|  
|`supportUrl`|Необязательный. Указывает URL-адрес поддержки, которое отображается в **Установка и удаление программ** панели управления. Ярлык на этот URL-адрес также создается для поддержки приложения в Windows **запустить** меню, когда развертывание настроено для установки.|  
  
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