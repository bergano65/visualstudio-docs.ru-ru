---
title: "Пользовательские инструменты | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Пакеты VSPackage, пользовательские инструменты"
  - "пользовательские средства [Visual Studio]"
  - "пользовательские инструменты"
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Пользовательские инструменты
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

*Пользовательские инструменты* let необходимо связать средство с элементом проекта и запустить средство, если файл сохранен.  Некоторые пользовательские средства, иногда называемые *генераторов одного файла*часто используется для реализации переводчиков, которые создают код из данных, и наоборот.  Например, генераторов одного файла создают [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] исходный код из файлов .settings и resx.  Созданный код источника предоставляет строго типизированный доступ к данным в файлах .settings и resx.  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] средства поддержки пользовательских типов проектов;  [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] типы проектов.  Собственные типы проектов могут также поддерживать настраиваемые средства.  
  
 Пользовательские инструменты зарегистрированные компоненты, которые реализуют `IVsSingleFileGenerator` интерфейс.  
  
 Пользовательские инструменты связанные с a `ProjectItem` объект интерфейса и как конструкторы, редакторы.  Пользовательский инструмент принимает файл, представленный a `ProjectItem` на входе и записи нового файла, для которого задано имя файла  `DefaultExtension` метод.  
  
## В этом подразделе  
 [Реализация генераторов одного файла](../../extensibility/internals/implementing-single-file-generators.md)  
 Описывает использование <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> интерфейс, чтобы реализовать пользовательское средство.  
  
 [Определение пространства имен по умолчанию для проекта](../../misc/determining-the-default-namespace-of-a-project.md)  
 Описывает, как указать соответствующее пространство имен в зависимости от используемого языка.  
  
 [Регистрация генераторов одного файла](../../extensibility/internals/registering-single-file-generators.md)  
 Содержит описания всех записей реестра для пользовательского инструмента.  
  
 [Предоставление визуальные конструкторы типов](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 Описание системы проектов предоставляют поддержку для визуальных конструкторах к классам и типам, созданным доступом через временные переносимые файлы исполняемый файл \(PE\).  
  
 [Сохранение свойства элемента проекта](../../extensibility/persisting-the-property-of-a-project-item.md)  
 Показано, как сохранить свойство элемента проекта, например автору исходного файла в файле проекта.  
  
## Ссылка  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 Предоставляет сведения о <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>, который преобразует один входной файл в одновыходовой файл, который можно компилировать и добавлен в проект.  
  
 <xref:EnvDTE.ProjectItem>  
 Описание `ProjectItem` интерфейс, представляющий элемент проекта.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 Предоставляет сведения о `DefaultExtension` метод, который получает расширение имени файла, которое назначается имя файла вывода.  
  
## Связанные подразделы  
 [Расширение проектов](../../extensibility/extending-projects.md)  
 Описывает использование [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проекты и решения упорядочить файлы кода и файлы ресурсов, а также, как реализовать систему управления версиями.