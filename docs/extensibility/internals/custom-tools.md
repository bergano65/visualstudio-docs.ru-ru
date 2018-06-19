---
title: Пользовательские инструменты | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 5f215cfbd5113377e7a98439976a7f44215eee02
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128888"
---
# <a name="custom-tools"></a>Пользовательские средства
*Пользовательские средства* позволяют средство, связанные с элементом в проекте и запуска этого средства, при каждом сохранении файла. Некоторые пользовательские средства иногда называют *генераторы одного файла*, часто используются для реализации трансляторы, создающих код на основе данных и наоборот. Например, создать один файл генераторы [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] в исходном коде от .settings и RESX-файлов. Созданный исходный код предоставляет строго типизированный доступ к данным в файлах с расширением Settings и .resx. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] И [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] типов проектов поддерживают пользовательские средства; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] типы проектов — нет. Собственные типы проектов также могут поддерживать пользовательские средства.  
  
 Пользовательские средства, зарегистрированных компонентов, реализующих `IVsSingleFileGenerator` интерфейса.  
  
 Пользовательские средства связаны с `ProjectItem` объекта интерфейса и, как редакторы и конструкторы. Пользовательский инструмент принимает файл, представленный `ProjectItem` качестве входных данных и записывает новый файл, имя которого обеспечивается `DefaultExtension` метод.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Реализация генераторов одного файла](../../extensibility/internals/implementing-single-file-generators.md)  
 Описывает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс для реализации пользовательского инструмента.  
  
 [Регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md)  
 Содержит описание всех записей реестра для пользовательского инструмента.  
  
 [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Объясняет, как проект системы предоставляют поддержку для визуальные конструкторы для доступа созданных классов и типов через файлы временной переносимого исполняемого (PE).  
  
 [Сохранение свойства элемента проекта](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Показано, как сохранить свойства элемента проекта, например автору исходного файла, в файле проекта.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Предоставляет подробные сведения о <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, преобразующий одного входного файла в один выходной файл, который компилируется или добавить в проект.  
  
 <xref:EnvDTE.ProjectItem>  
 Объясняет `ProjectItem` интерфейс, который представляет элемент в проект.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Предоставляет подробные сведения о `DefaultExtension` метод, который получает расширение имени файла, которое присвоено имя выходного файла.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Расширение проектов](../../extensibility/extending-projects.md)  
 Описывает использование [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекты и решения для организации файлов кода и файлов ресурсов и способы реализации системы управления версиями.