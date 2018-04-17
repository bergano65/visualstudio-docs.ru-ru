---
title: '&lt;vstoRuntime&gt; элемент (Разработка решений Office в Visual Studio) | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ee2d50d69c363d5073a09b953c00d22a11ef5315
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime&gt; элемент (Разработка решений Office в Visual Studio)
  Элемент `vstoRuntime` пространства имен `vstav3` содержит версию среды выполнения Набора инструментов Visual Studio для Office, поддерживаемую конкретным решением Office.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `vstoRuntime` является обязательным и находится в пространстве имен `vstav3` . Если решение Office поддерживает две версии среды выполнения Набора инструментов Visual Studio для Office, в манифесте приложения будет два элемента `vstoRuntime` .  
  
 Элемент `vstoRuntime` имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`release`|Обязательно. Выпускаемая версия среды выполнения Набора инструментов Visual Studio для Office.|  
|`version`|Обязательно. Номер версии среды выполнения Набора инструментов Visual Studio для Office.|  
|`supportUrl`|Необязательный. Ссылка на расположение установки среды выполнения Набора инструментов Visual Studio для Office.|  
  
 Элемент`vstoRuntime` не содержит элементов.  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере кода показан элемент `vstoRuntime` манифеста приложения для решения Office, развертываемого с помощью [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Этот пример кода является частью большего примера, приведенного в разделе [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>См. также  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Манифесты развертывания для решений Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Манифест приложения ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  