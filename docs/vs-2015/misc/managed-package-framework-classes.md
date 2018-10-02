---
title: Классы Managed Package Framework | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: 38f159df52c99554ed931269f29ad57e72745b5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571093"
---
# <a name="managed-package-framework-classes"></a>Классы Managed Package Framework
Классы Managed Package Framework (MPF) можно использовать для создания пакетов VSPackage с помощью управляемого кода. Они предоставляют реализации по умолчанию для многих интерфейсов VSPackage. Скрывая детали и сложности реализации, MPF позволяет создавать [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] продукты интеграции с помощью минимального количества кода.  
  
> [!WARNING]
>  Большинство сборок, содержащих классы MPF, поставляются вместе с Visual Studio SDK. Вы можете загрузить исходный код для MPF для проектов в разделе [Managed Package Framework для проектов](http://mpfproj11.codeplex.com/).  
  
## <a name="mpf-namespaces"></a>Пространства имен MPF  
 В следующей таблице перечислены пространства имен MPF, предоставляемые [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Пространство имен|Описание|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Содержит полезные классы для обработки ошибок COM, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] константы и окон Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Включает оболочки управляемого кода для [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проектов, редакторов и MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Включает базовые классы MPF, от которых можно производить реализацию многих распространенных объектов Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Содержит [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширения конструктора.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Содержит [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширения конструктора сериализации.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Содержит [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширения конструктора CodeDom.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Поддерживает подтипы проекта (также называемые "версиями").|  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage и Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)   
 [С помощью сборок взаимодействия Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Пакеты VSPackage и Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)