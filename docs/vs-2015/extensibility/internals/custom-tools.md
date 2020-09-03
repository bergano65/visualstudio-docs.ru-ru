---
title: Настраиваемые инструменты | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 594d564cf4a18eb0b673abd9b45b7d70e20381b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196922"
---
# <a name="custom-tools"></a>Настраиваемые средства
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

*Пользовательские средства* позволяют связать средство с элементом в проекте и запускать его при каждом сохранении файла. Некоторые пользовательские средства, иногда называемые *генераторами с одним файлом*, часто используются для реализации переводчиков, создающих код на основе данных и наоборот. Например, генераторы с одним файлом создают [!INCLUDE[csprcs](../../includes/csprcs-md.md)] и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] исключают исходный код из файлов. Settings и. resx. Созданный исходный код предоставляет строго типизированный доступ к данным в файлах. Settings и. resx. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Типы проектов и поддерживают пользовательские средства; [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] типы проектов — нет. Собственные типы проектов также могут поддерживать пользовательские средства.  
  
 Пользовательские средства — это зарегистрированные компоненты, реализующие `IVsSingleFileGenerator` интерфейс.  
  
 Пользовательские инструменты связаны с `ProjectItem` объектом интерфейса и подобны конструкторам и редакторам. Пользовательский инструмент принимает файл, представленный в `ProjectItem` качестве входных данных, и записывает новый файл, имя которого предоставляется `DefaultExtension` методом.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Реализация генераторов одного файла](../../extensibility/internals/implementing-single-file-generators.md)  
 Описывает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейса для реализации пользовательского инструмента.  
  
 [Определение пространства имен по умолчанию для проекта](../../misc/determining-the-default-namespace-of-a-project.md)  
 Описывает, как определить правильное пространство имен на основе используемого языка.  
  
 [Регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md)  
 Содержит описания всех записей реестра для пользовательского инструмента.  
  
 [Предоставление типов конструкторам визуальных элементов](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Объясняет, как системы проектов обеспечивают поддержку визуальных конструкторов для доступа к создаваемым классам и типам через временные переносимые исполняемые файлы (PE).  
  
 [Сохранение свойства элемента проекта](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Показывает, как сохранить свойство элемента проекта, например автора исходного файла, в файле проекта.  
  
## <a name="reference"></a>Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Предоставляет подробные сведения о компоненте <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , который преобразует один входной файл в отдельный выходной файл, который может быть скомпилирован или добавлен в проект.  
  
 <xref:EnvDTE.ProjectItem>  
 Описывает `ProjectItem` интерфейс, который представляет элемент в проекте.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Предоставляет подробные сведения о `DefaultExtension` методе, который извлекает расширение имени файла, присвоенное имени выходного файла.  
  
## <a name="related-sections"></a>См. также  
 [Расширение проектов](../../extensibility/extending-projects.md)  
 Описывается использование проектов и решений [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для организации файлов кода и файлов ресурсов, а также реализация системы управления версиями.
