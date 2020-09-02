---
title: '&lt;&gt;элемент кустомерроррепортинг (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7e8a0db3e10a277fe1c4a2f8fcd2bb85fa69e69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187828"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;&gt;элемент кустомерроррепортинг (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задает отображаемый в случае ошибки URI.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<customErrorReporting  
   uri  
/>  
```  
  
## <a name="remarks"></a>Remarks  
 Этот элемент является необязательным. Без него [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] отображает диалоговое окно ошибки, в котором отображается стек исключений. Если `customErrorReporting` элемент имеется, то [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] вместо этого отображает URI, указанный `uri` параметром. Целевой URI будет включать класс внешнего исключения, класс внутреннего исключения и сообщение внутреннего исключения в качестве параметров.  
  
 Используйте этот элемент, чтобы добавить в приложение функцию создания отчетов об ошибках. Так как созданный универсальный код ресурса (URI) содержит сведения о типе ошибки, веб-сайт может проанализировать эту информацию и отобразить, например, соответствующий экран устранения неполадок.  
  
## <a name="example"></a>Пример  
 В следующем фрагменте кода показан `customErrorReporting` элемент вместе с созданным URI, который он может создать.  
  
```  
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />  
  
Example Generated Error:  
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.  
```  
  
## <a name="see-also"></a>См. также:  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
