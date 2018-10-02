---
title: Элементы модели проекта | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c3c26bb501e28c324233e4991fc8023b2adcdcf6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571605"
---
# <a name="elements-of-a-project-model"></a>Элементы модели проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элементы модели проекта](https://docs.microsoft.com/visualstudio/extensibility/internals/elements-of-a-project-model).  
  
Интерфейсы и реализации всех проектов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] совместно использовать базовую структуру: модель проекта для данного типа проекта. В модели проекта, являющийся VSPackage, при разработке, создании объектов, соответствующих проектные решения и работающих вместе с глобальных функций, предоставляемых интегрированной среды разработки. Несмотря на то, что вы управляете, как сохраняется элемент проекта, например, уведомления, что файл должен сохраняться не управлять. Когда пользователь помещает фокус на элемент Открытие проекта и выбирает **Сохранить** на **файл** меню [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] меню панели код типа проекта необходимо перехватывать команды из интегрированной среды разработки, сохранится файл, и отправьте уведомление обратно в интегрированной среде разработки, что файл не изменен.  
  
 VSPackage взаимодействует с интегрированной средой разработки через службы, которые предоставляют доступ к интерфейсам интегрированной среды разработки. Например посредством определенных служб, монитор и маршрута команд и предоставляют сведения о контексте для выбора, сделанного в проект. Все глобальные функции интегрированной среды разработки, необходимые для вашего VSPackage, предоставляемый службами. Дополнительные сведения о службах см. в разделе [как: доступ к службе](../../extensibility/how-to-get-a-service.md).  
  
 Другие вопросы реализации:  
  
-   Модель одного проекта может содержать более одного типа проекта.  
  
-   Типы проектов и фабрик помощника проектов независимо друг от друга регистрируются с идентификаторами GUID.  
  
-   Каждый проект должен содержать файл шаблона или мастер, чтобы инициализировать новый файл проекта, когда пользователь создает новый проект через [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пользовательского интерфейса. Например [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] шаблоны инициализации, что со временем стать VCPROJ-файлами.  
  
 Ниже показаны интерфейсы, службы и объекты, которые составляют реализацию типичный проект. Вспомогательные приложения, HierUtil7, можно использовать для создания базовых объектов и других программирования шаблона. Дополнительные сведения о HierUtil7 вспомогательного приложения, см. в разделе [не в сборке: использование HierUtil7 проект классов для реализации типа проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![График Visual Studio проект модели](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
модель проекта  
  
 Дополнительные сведения о интерфейсов и служб, перечисленных в предыдущей схеме и других дополнительных интерфейсов, не включенных в диаграмму, см. в разделе [основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md).  
  
 Проекты может поддерживать команды и поэтому необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для участия в маршрутизации команд через контекст команды идентификаторы GUID.  
  
## <a name="see-also"></a>См. также  
 [Контрольный список: Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Не в сборке: использование HierUtil7 проект классов для реализации типа проекта (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)   
 [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Практическое: Получение службы](../../extensibility/how-to-get-a-service.md)   
 [Создание типов проектов](../../extensibility/internals/creating-project-types.md)

