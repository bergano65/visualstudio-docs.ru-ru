---
title: "Подтипы проектов | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "проекты [Visual Studio SDK] подтипы"
  - "подтипы проектов [Visual Studio SDK]"
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Подтипы проектов
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Подтипы проектов позволяют настраивать или поведение системы проекта flavor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Настройки включают сохранение дополнительных данных в файле проекта, добавляя или фильтруя элементы в **Добавление нового элемента** диалоговом управление как отладки и развертывания сборки и расширение проекта **страницы свойств** диалоговое окно. Пакеты VSPackage реализовать подтипы проектов с помощью COM статистической обработки.  
  
> [!NOTE]
>  Система проектов Visual C\+\+ не поддерживает подтипы проектов.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] подтипы проектов используется для реализации проектов для смарт\-устройств и SQL Server.  
  
## В этом подразделе  
 [Подтипы разработки проекта](../../extensibility/internals/project-subtypes-design.md)  
 Описание концепции проекта подтипы.  
  
 [Последовательность инициализации подтипы проектов](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Описывает последовательность инициализации подтип программного проекта, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среду.  
  
 [Свойства и методы дополнено подтипы проектов](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Содержит подробное описание функций и методов, наиболее часто расширены с помощью проекта подтипы.  
  
 [Сохранение данных в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Описывает способы сохранения данных в файл проекта и использовать <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> для сохранения данных в файле проекта через уровни статистической обработки подтип проекта.  
  
 [Пользовательский интерфейс свойства проекта](../../extensibility/internals/project-property-user-interface.md)  
 Описывает, как подтипы проектов можно изменить проект **страницы свойств** диалоговое окно.  
  
 [Расширение модели объекта базового проекта](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Сведения о как проект подтипы расширители автоматизации можно использовать для расширения модели объектов автоматизации.  
  
 [Способствовали добавить новый элемент\-диалоговое окно](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Описывает, как добавлять элементы в **Добавление нового элемента** диалоговое окно.  
  
 [Сохранение данных в файлах проектов](../../extensibility/saving-data-in-project-files.md)  
 Объясняет, как подтипом проекта можно сохранять и извлекать подтипа данных в файле проекта с помощью управляемых пакета Framework \(MPF\).  
  
 [Обработка специализированные развертывания](../../extensibility/internals/handling-specialized-deployment.md)  
 Объясняет, как подтипы проекта можно указать поведение специализированные развертывания путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> интерфейса.  
  
 [Добавление и удаление страницы свойств](../../extensibility/adding-and-removing-property-pages.md)  
 Описывает добавление и удаление страниц свойств в конструкторе проектов.  
  
## Связанные подразделы  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Ссылки на разделы с подробными сведениями о [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проектов.