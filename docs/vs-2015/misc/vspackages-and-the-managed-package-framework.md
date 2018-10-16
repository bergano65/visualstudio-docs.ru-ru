---
title: Пакеты VSPackage и Managed Package Framework | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework
- VSPackages, managed package framework
- managed VSPackages, managed package framework
ms.assetid: e8d80e0f-6b5b-4baf-a7df-59fd808c60cd
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: 2e265a342ec32abea40ab9b352b5735079462a46
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227985"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Пакеты VSPackage и Managed Package Framework
Путем создания VSPackage в управляемом пакете классов framework (MPF), а не с помощью COM-взаимодействия классов можно сократить время разработки.  
  
 Создание управляемого пакета VSPackage двумя способами:  
  
-   Используйте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] шаблон проекта пакета  
  
     Дополнительные сведения см. в разделе [Пошаговое руководство: Создание меню команды с использованием шаблона пакета Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
-   Создание VSPackage без [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] шаблон проекта пакета  
  
     Например можно скопировать образец пакета VSPackage и изменить имена и идентификаторы GUID. Примеры можно найти в разделе VSX [коллекции исходных кодов](http://code.msdn.microsoft.com/vsx/).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Классы Managed Package Framework](../misc/managed-package-framework-classes.md)  
 Описание и перечислены пространства имен MPF класс и DLL-файлы.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Пошаговое руководство: Создание команды меню с помощью шаблона пакета Visual Studio](http://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 В этой статье описывается создание управляемого пакета VSPackage.  
  
 [Управляемые пакеты VSPackage](../misc/managed-vspackages.md)  
 Представляет аспекты пакеты VSPackage, которые применяются к управляемому коду.