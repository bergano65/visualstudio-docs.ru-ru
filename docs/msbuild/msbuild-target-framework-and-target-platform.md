---
title: "MSBuild: целевая рабочая среда и целевая платформа | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: f91e102854a83cc70e7b7f4adbc2cd2afb727b07
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild: целевая рабочая среда и целевая платформа
Проект может быть создан для выполнения в *требуемой версии .NET Framework*, которая является конкретной версией платформы .NET Framework, и на *целевой платформе*, которая является конкретной программной архитектурой.  Например, можно настроить приложение для выполнения в .NET Framework 2.0 на 32-разрядной платформе, которая совместима с семейством процессоров 802x86 («x86»). Сочетание требуемой версии .NET Framework и целевой платформы называется *целевым контекстом*.  
  
## <a name="target-framework-and-profile"></a>Целевая платформа и профиль  
 Целевая платформа — это конкретная версия [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], для выполнения на которой создан проект. Спецификация целевой платформы является необходимым условием, поскольку она позволяет использовать возможности компилятора и ссылки на сборки, предназначенные исключительно для этой версии платформы.  
  
 В настоящее время доступны следующие версии платформы .NET Framework.  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 (входит в состав Visual Studio 2005)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.0 (входит в состав [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 (входит в состав [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 (входит в состав Visual Studio 2010)  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5 (входит в состав [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.5.1 (входит в состав [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)])  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]4.5.2  
  
-   [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.6 (входит в состав [!INCLUDE[vs_dev14](../misc/includes/vs_dev14_md.md)])  
  
 Версии платформы .NET Framework отличаются друг от друга в списке сборок, доступном для использования в справочных целях. Например, приложения WPF можно создавать, только если проект предназначен для платформы .NET Framework версии 3.0 или выше.  
  
 Целевая версия .NET Framework указывается в свойстве `TargetFrameworkVersion` в файле проекта. Целевую версию .NET Framework для проекта можно изменить с помощью страниц свойств проекта в интегрированной среде разработки Visual Studio. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Доступными значениями для `TargetFrameworkVersion` являются `v2.0`, `v3.0`, `v3.5`, `v4.0`, `v4.5`, `v4.5.1`, `v4.5.2` и `v4.6`.  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 *Целевой профиль* — это подмножество целевой платформы. Например, профиль клиента .NET Framework 4 не содержит ссылок на сборки MSBuild.  
  
 Целевой профиль указывается в свойстве `TargetFrameworkProfile` в файле проекта. Целевой профиль можно изменить с помощью элемента управления целевой платформы на страницах свойств проекта в интегрированной среде разработки. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```xml  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Целевая платформа  
 *Платформа* — это сочетание оборудования и программного обеспечения, которое определяет конкретную среду выполнения. Например:  
  
-   `x86` обозначает 32-разрядную операционную систему Windows, работающую с процессором Intel 80x86 или эквивалентным.  
  
-   `Xbox` обозначает платформу Microsoft Xbox 360.  
  
 *Целевая платформа* — это конкретная платформа, для выполнения на которой создан проект. Целевая платформа указывается в свойстве сборки `Platform` в файле проекта. Целевую платформу можно изменить с помощью страниц свойств проекта или **диспетчера конфигураций** в интегрированной среде разработки.  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 *Целевая конфигурация* — это подмножество целевой платформы. Например, конфигурация `x86``Debug` не поддерживает большинство видов оптимизации кода. Целевая конфигурация указывается в свойстве сборки `Configuration` в файле проекта. Целевую конфигурацию можно изменить с помощью страниц свойств проекта или **диспетчера конфигураций**.  
  
```xml  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)
