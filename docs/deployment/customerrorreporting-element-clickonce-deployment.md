---
title: '&lt;&gt;элемент кустомерроррепортинг (развертывание ClickOnce) | Документация Майкрософт'
description: Элемент Кустомерроррепортинг указывает URI, который будет отображаться при возникновении ошибки, а не в диалоговом окне ошибки, отображающем стек исключений.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b168b3bcb90ae758609698de306928eb7e13d909
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888489"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;&gt;элемент кустомерроррепортинг (развертывание ClickOnce)
Задает отображаемый в случае ошибки URI.

## <a name="syntax"></a>Синтаксис

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Remarks
 Этот элемент является необязательным. Без него [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] отображает диалоговое окно ошибки, в котором отображается стек исключений. Если `customErrorReporting` элемент имеется, то [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] вместо этого отображает URI, указанный `uri` параметром. Целевой URI будет включать класс внешнего исключения, класс внутреннего исключения и сообщение внутреннего исключения в качестве параметров.

 Используйте этот элемент, чтобы добавить в приложение функцию создания отчетов об ошибках. Так как созданный универсальный код ресурса (URI) содержит сведения о типе ошибки, веб-сайт может проанализировать эту информацию и отобразить, например, соответствующий экран устранения неполадок.

## <a name="example"></a>Пример
 В следующем фрагменте кода показан `customErrorReporting` элемент вместе с созданным URI, который он может создать.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>См. также раздел
- [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)