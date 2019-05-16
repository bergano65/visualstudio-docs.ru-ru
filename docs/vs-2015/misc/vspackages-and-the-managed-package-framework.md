---
title: Пакеты VSPackage и Managed Package Framework | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 5b72b2c3bd6b03d1d3f3e50135c2ddf4758a4bd9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683044"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Пакеты VSPackage и Managed Package Framework
Путем создания VSPackage в управляемом пакете классов framework (MPF), а не с помощью COM-взаимодействия классов можно сократить время разработки.  
  
 Создание управляемого пакета VSPackage двумя способами:  
  
- Используйте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] шаблон проекта пакета  
  
     Дополнительные сведения см. в разделе [Пошаговое руководство: Создание команды меню с помощью шаблона пакета Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Создание VSPackage без [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] шаблон проекта пакета  
  
     Например можно скопировать образец пакета VSPackage и изменить имена и идентификаторы GUID. Примеры можно найти в разделе VSX [коллекции исходных кодов](http://code.msdn.microsoft.com/vsx/).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Классы Managed Package Framework](../misc/managed-package-framework-classes.md)  
 Описание и перечислены пространства имен MPF класс и DLL-файлы.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Пошаговое руководство: Создание команды меню с помощью шаблона пакета Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 В этой статье описывается создание управляемого пакета VSPackage.  
  
 [Управляемые пакеты VSPackage](../misc/managed-vspackages.md)  
 Представляет аспекты пакеты VSPackage, которые применяются к управляемому коду.