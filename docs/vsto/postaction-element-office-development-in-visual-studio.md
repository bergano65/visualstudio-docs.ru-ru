---
title: "&lt;postAction&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
ms.assetid: a047e2e2-9732-4140-b8bd-bc5bd1b84291
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 581ef7bafc075419df8e2dfb1731b334a9564455
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `postAction` пространства имен `vstav3` содержит элементы `entrypoint` и все элементы `postActionData` , связанные с действиями после развертывания, которые выполняются после установки решений Office.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<postAction>  
  <entryPoint>  
  </entryPoint>  
  <postActionData>  
  </postActionData>  
</postAction>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `postAction` является необязательным и находится в пространстве имен `vstav3` . В манифесте приложения определяется один элемент `postAction` для каждого выполняемого после развертывания действия.  
  
 У элемента `postAction` нет атрибутов.  
  
 У элемента`postAction` имеются перечисленные ниже элементы.  
  
### <a name="entrypoint"></a>entrypoint  
 Необязательно. Роль `entryPoint` элемент в `vstav3` пространство имен определяется в [&#60; entryPoints &#62; Элемент &#40; разработка решений Office в Visual Studio &#41; ](../vsto/entrypoints-element-office-development-in-visual-studio.md).  
  
### <a name="postactiondata"></a>postActionData  
 Необязательно. Роль `postActionData` элемент в `vstav3` пространство имен определяется в [&#60; postActionData &#62; Элемент &#40; разработка решений Office в Visual Studio &#41; ](../vsto/postactiondata-element-office-development-in-visual-studio.md).  
  
## <a name="post-deployment-action-example"></a>Пример действия, выполняемого после развертывания  
  
### <a name="description"></a>Описание  
 В приведенном ниже примере кода показан элемент `postAction` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Код  
  
```  
<vstav3:postAction>  
  <vstav3:entryPoint   
    class="PostDeploymentAction.PostDeploymentActionSample">  
    <assemblyIdentity   
      name="PostDeploymentAction"   
      version="1.0.0.0"   
      language="neutral"   
      processorArchitecture="msil" />  
  </vstav3:entryPoint>  
  <vstav3:postActionData>  
  </vstav3:postActionData>  
</vstav3:postAction>  
```  
  
## <a name="see-also"></a>См. также  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  