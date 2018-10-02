---
title: Пользовательские инструменты | Документация Майкрософт
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
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72fb6f9f0ceb3b9f2ae04f39b2c37c416acf47b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561944"
---
# <a name="custom-tools"></a>Настраиваемые средства
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [средства пользовательских](https://docs.microsoft.com/visualstudio/extensibility/internals/custom-tools).  
  
*Пользовательские средства* позволяют связать с элементом в проекте это средство и запускать это средство, при каждом сохранении файла. Некоторые пользовательские инструменты, иногда называют *генераторов одного файла*, часто используются для реализации преобразователей, создающих код на основе данных и наоборот. Например, создать генераторов одного файла [!INCLUDE[csprcs](../../includes/csprcs-md.md)] и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] исходный код от .settings и RESX-файлов. Созданный исходный код предоставляет строго типизированный доступ к данным в .settings и RESX-файлах. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] И [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] типов проектов поддерживают пользовательские средства; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] типы проектов — нет. Собственные типы проектов также может поддерживать пользовательские инструменты.  
  
 Пользовательские инструменты, зарегистрированных компонентов, которые реализуют `IVsSingleFileGenerator` интерфейс.  
  
 Пользовательские средства связаны с `ProjectItem` объекта интерфейса и, как редакторы и конструкторы. Настраиваемое средство принимает файл, представленный `ProjectItem` качестве входных данных и создает новый файл, имя которого обеспечивается `DefaultExtension` метод.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Реализация генераторов одного файла](../../extensibility/internals/implementing-single-file-generators.md)  
 Описывает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс для реализации пользовательского инструмента.  
  
 [Определение пространства имен по умолчанию для проекта](../../misc/determining-the-default-namespace-of-a-project.md)  
 Описывает способ определить правильное пространство имен, в зависимости от используемого языка.  
  
 [Регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md)  
 Содержит описание всех записей реестра для пользовательского средства.  
  
 [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Объясняет, как системы проектов поддерживают визуальные конструкторы для доступа созданных классов и типов через временный переносимый исполняемый файл (PE) файлов.  
  
 [Сохранение свойства элемента проекта](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Показан способ сохранения свойства элемента проекта, например автора исходного файла, в файле проекта.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Предоставляет сведения о <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, который преобразует одного входного файла в один выходной файл, который можно скомпилировать и добавить в проект.  
  
 <xref:EnvDTE.ProjectItem>  
 Объясняет `ProjectItem` интерфейс, который представляет элемент в проекте.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Предоставляет сведения о `DefaultExtension` метод, который получает расширение имени файла, который назначается имя выходного файла.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Расширение проектов](../../extensibility/extending-projects.md)  
 Описывает использование [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проекты и решения для организации файлов кода и файлов ресурсов и способы реализации системы управления версиями.

