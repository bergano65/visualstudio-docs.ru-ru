---
title: Пользовательские инструменты Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708957"
---
# <a name="custom-tools"></a>Специальные инструменты
*Пользовательские инструменты* позволяют связать инструмент с элементом в проекте и запустить этот инструмент всякий раз, когда файл сохраняется. Некоторые пользовательские инструменты, иногда называемые *генераторами одного файла,* часто используются для реализации переводчиков, которые генерируют код из данных и наоборот. Например, генераторы с одним [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] файлами создают и исходируют код из файлов *.setting* и *.resx.* Генерируемый исходный код обеспечивает сильно набранный доступ к данным в *параметрах .setting s* и *.resx.* [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Типы [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проектов поддерживают пользовательские инструменты; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] типы проектов этого не делают. Ваши собственные типы проектов также могут поддерживать пользовательские инструменты.

 Пользовательские инструменты являются `IVsSingleFileGenerator` зарегистрированными компонентами, которые реализуют интерфейс.

 Пользовательские инструменты `ProjectItem` связаны с объектом интерфейса и подобны дизайнерам и редакторам. Пользовательский инструмент забирает файл, представленный вводимым `ProjectItem` и записывает `DefaultExtension` новый файл, имя файла которого предоставляется методом.

## <a name="in-this-section"></a>В этом разделе
- [Внедрение генераторов с одним файлами](../../extensibility/internals/implementing-single-file-generators.md)

 Описывает, как <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> использовать интерфейс для реализации пользовательского инструмента.

- [Регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md)

 Предоставляет описания для всех записей реестра для пользовательского инструмента.

- [Экспозиция типов для визуальных дизайнеров](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Объясняет, как проектные системы обеспечивают поддержку визуальных дизайнеров для доступа к генерируемым классам и типам через временные портативные исполняемые (PE) файлы.

- [Сохранение свойства элемента проекта](../../extensibility/persisting-the-property-of-a-project-item.md)

 Показано, как сохранить свойство элемента проекта, например автора исходного файла, в файле проекта.

## <a name="reference"></a>Справочник
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Предоставляет подробную <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>информацию о , который преобразует один файл ввода в единый выходный файл, который может быть скомпилирован или добавлен в проект.

 <xref:EnvDTE.ProjectItem>Объясняет `ProjectItem` интерфейс, представляющий элемент в проекте.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Предоставляет подробную `DefaultExtension` информацию о методе, который получает расширение имени файла, которое дается имени вывода файла.

## <a name="related-sections"></a>См. также
- [Расширение проектов](../../extensibility/extending-projects.md)

 Описывается использование проектов и решений [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] для организации файлов кода и файлов ресурсов, а также реализация системы управления версиями.
