---
title: Классы платформы управляемых пакетов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: 2e9fe1abb82d3d64232e3e5e2a6d117c1068aa1c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297694"
---
# <a name="managed-package-framework-classes"></a>Классы Managed Package Framework
Классы Managed Package Framework (MPF) можно использовать для создания пакетов VSPackage с помощью управляемого кода. Они предоставляют реализации по умолчанию для многих интерфейсов VSPackage. Скрывая детали и сложности реализации, MPF позволяет создавать продукты интеграции [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с минимальным объемом кода.  
  
> [!WARNING]
> Большинство сборок, содержащих классы MPF, поставляются вместе с Visual Studio SDK. Вы можете загрузить исходный код для MPF для проектов в разделе [Managed Package Framework для проектов](https://archive.codeplex.com/?p=mpfproj11).  
  
## <a name="mpf-namespaces"></a>Пространства имен MPF  
 В следующей таблице перечислены пространства имен MPF, предоставляемые [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Пространство имен|Содержание|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Содержит полезные классы для обработки ошибок COM, констант [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и окон Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Включает оболочки управляемого кода для проектов, редакторов и MSBuild [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell>|Включает базовые классы MPF, от которых можно производить реализацию многих распространенных объектов Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Содержит расширения конструктора [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Содержит расширения конструктора сериализации [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Содержит расширения конструктора CodeDom [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Поддерживает подтипы проекта (также называемые "версиями").|  
  
## <a name="see-also"></a>См. также  
 [Пакеты VSPackage и управляемая платформа пакетов](../misc/vspackages-and-the-managed-package-framework.md)   
 [Использование сборок взаимодействия Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Пакеты VSPackage и Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)