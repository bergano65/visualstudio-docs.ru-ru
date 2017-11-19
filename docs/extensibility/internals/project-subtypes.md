---
title: "Подтипы проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 84d2700e1dfb5d66fb2df6376db9e0ce5352ad4e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="project-subtypes"></a>Подтипы проектов
Подтипы проекта позволяют настраивать или flavor поведение системы проектов из [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Настройки включают сохранение дополнительных данных в файле проекта, добавления или фильтрации элементов в **Добавление нового элемента** диалоговом управление как отладки и развертывания сборок и расширение проекта **свойство Страницы** диалоговое окно. Пакеты VSPackage реализовывать подтипы проекта с помощью COM статистической обработки.  
  
> [!NOTE]
>  Система проектов Visual C++ не поддерживает подтипы проекта. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]подтипы проекта сам использует для реализации проектов SQL Server и смарт-устройств.  
  
## <a name="in-this-section"></a>Содержание  
 [Разработка подтипов проекта](../../extensibility/internals/project-subtypes-design.md)  
 Описание концепции подтипы проекта.  
  
 [Инициализация последовательности подтипов проекта](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Описывает последовательность инициализации подтип программный проекта по [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среды.  
  
 [Свойства и методы, расширенные подтипами проектов](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Содержит подробное описание функции и методы, наиболее часто расширены с помощью подтипы проекта.  
  
 [Сохранение данных в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Описывается, как для сохранения данных в файл проекта и использовании <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> для сохранения данных в файле проекта разных уровнях статистической обработки подтип проекта.  
  
 [Пользовательский интерфейс свойств проекта](../../extensibility/internals/project-property-user-interface.md)  
 Описывает, как подтипы проекта можно изменить проект **страницы свойств** диалоговое окно.  
  
 [Расширение модели объекта базового проекта](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Сведения о как подтипы проекта расширители автоматизации можно использовать для расширения модели объектов автоматизации.  
  
 [Добавление элементов в диалоговое окно "Добавление новых элементов"](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Описывает, как добавить элементы в **Добавление нового элемента** диалоговое окно.  
  
 [Сохранение данных в файлах проектов](../../extensibility/saving-data-in-project-files.md)  
 Объясняет, как подтипом проекта можно сохранять и извлекать подтипа данных в файле проекта с помощью Managed Package Framework (MPF).  
  
 [Обработка специализированного развертывания](../../extensibility/internals/handling-specialized-deployment.md)  
 Объясняет, как подтипы проекта можно указать поведение при развертывании специализированных путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> интерфейса.  
  
 [Добавление и удаление страниц свойств](../../extensibility/adding-and-removing-property-pages.md)  
 Описание добавления и удаления страницы свойств в конструкторе проектов.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Ссылки на разделы с подробными сведениями о [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проектов.