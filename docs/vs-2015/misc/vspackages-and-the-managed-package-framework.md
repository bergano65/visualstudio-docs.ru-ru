---
title: Пакеты VSPackage и управляемая платформа пакетов | Документация Майкрософт
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
ms.openlocfilehash: 84fb41bfc80415535ca41d6b1a8c9dcf47124c7a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298228"
---
# <a name="vspackages-and-the-managed-package-framework"></a>Пакеты VSPackage и Managed Package Framework
Вы можете сократить время разработки, создав пакет VSPackage с классами Managed Package Framework (MPF), а не используя классы COM-взаимодействия.  
  
 Существует два способа создания управляемого пакета VSPackage:  
  
- Использование шаблона проекта пакета [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
     Дополнительные сведения см. [в разделе Пошаговое руководство. Создание команды меню с помощью шаблона пакета Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de).  
  
- Создайте пакет VSPackage без шаблона проекта пакета [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
     Например, можно скопировать пример VSPackage и изменить идентификаторы GUID и имена. 
  
## <a name="in-this-section"></a>В этом разделе  
 [Классы Managed Package Framework](../misc/managed-package-framework-classes.md)  
 Описывает и перечисляет пространства имен класса MPF и DLL-файлы.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Пошаговое руководство. Создание команды меню с помощью шаблона пакета Visual Studio](https://msdn.microsoft.com/library/1985fa7d-aad4-4866-b356-a125b6a246de)  
 Объясняет, как создать управляемый пакет VSPackage.  
  
 [Управляемые пакеты VSPackage](../misc/managed-vspackages.md)  
 Содержит описание аспектов пакетов VSPackage, которые применяются к управляемому коду.