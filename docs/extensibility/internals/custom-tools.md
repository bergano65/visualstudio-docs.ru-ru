---
title: Пользовательские инструменты | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8b18ee5c1c84b8e6480ffa9f91f739796f0991
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834416"
---
# <a name="custom-tools"></a>Пользовательские инструменты
*Пользовательские средства* позволяют связать с элементом в проекте это средство и запускать это средство, при каждом сохранении файла. Некоторые пользовательские инструменты, иногда называют *генераторов одного файла*, часто используются для реализации преобразователей, создающих код на основе данных и наоборот. Например, создать генераторов одного файла [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] исходный код из *.settings* и *.resx* файлов. Созданный исходный код предоставляет строго типизированный доступ к данным в *.settings* и *.resx* файлов. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] И [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] типов проектов поддерживают пользовательские средства; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] типы проектов — нет. Собственные типы проектов также может поддерживать пользовательские инструменты.  
  
 Пользовательские инструменты, зарегистрированных компонентов, которые реализуют `IVsSingleFileGenerator` интерфейс.  
  
 Пользовательские средства связаны с `ProjectItem` объекта интерфейса и, как редакторы и конструкторы. Настраиваемое средство принимает файл, представленный `ProjectItem` качестве входных данных и создает новый файл, имя которого обеспечивается `DefaultExtension` метод.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Реализация генераторов одного файла](../../extensibility/internals/implementing-single-file-generators.md)  
 Описывает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс для реализации пользовательского инструмента.  
  
 [Генераторы зарегистрировать одного файла](../../extensibility/internals/registering-single-file-generators.md)  
 Содержит описание всех записей реестра для пользовательского средства.  
  
 [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Объясняет, как системы проектов поддерживают визуальные конструкторы для доступа созданных классов и типов через временный переносимый исполняемый файл (PE) файлов.  
  
 [Сохранить свойство элемента проекта](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Показан способ сохранения свойства элемента проекта, например автора исходного файла, в файле проекта.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Предоставляет сведения о <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, который преобразует одного входного файла в один выходной файл, который можно скомпилировать и добавить в проект.  
  
 <xref:EnvDTE.ProjectItem>  
 Объясняет `ProjectItem` интерфейс, который представляет элемент в проекте.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Предоставляет сведения о `DefaultExtension` метод, который получает расширение имени файла, который назначается имя выходного файла.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Расширения проектов](../../extensibility/extending-projects.md)  
 Описывается использование проектов и решений [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для организации файлов кода и файлов ресурсов, а также реализация системы управления версиями.