---
title: "Основные возможности MSBuild | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
caps.latest.revision: "13"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 4395f4c82be689b1d573be44948e98711ba066c3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-concepts"></a>Основные возможности MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] предоставляет базовую схему XML, которую можно использовать для управления процессом сборки программного обеспечения, выполняемым платформой сборки. Чтобы указать компоненты в сборке и способ ее выполнения, используйте следующие четыре составляющие MSBuild: свойства, элементы, задачи и целевые объекты.  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Свойства MSBuild](../msbuild/msbuild-properties.md)|Содержит вводную информацию о свойствах и коллекциях свойств. Свойства представляют собой пары "ключ — значение", с помощью которых выполняется настройка сборок.|  
|[Элементы](../msbuild/msbuild-items.md)|Содержит описание общих понятий, относящихся к формату файлов [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], и способов взаимодействия фрагментов.|  
|[Целевые объекты](../msbuild/msbuild-targets.md)|Содержит объяснение группировки задач в определенном порядке и вызова разделов процесса построения из командной строки.|  
|[Задачи](../msbuild/msbuild-tasks.md)|Описывает процесс создания блока исполняемого кода, с помощью которого [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] выполняет атомарные операции построения.|  
|[Сравнение свойств и элементов](../msbuild/comparing-properties-and-items.md)|Сравнивает свойства и элементы MSBuild. И то, и другое используется для передачи данных задачам, проверки условий и хранения значений, которые будут использоваться в файле проекта.|  
|[Специальные символы в MSBuild](../msbuild/msbuild-special-characters.md)|Объясняет, как записывать некоторые символы, зарезервированные [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] для специального применения в определенных контекстах, в виде escape-последовательностей.|  
|[Пошаговое руководство. Создание файла проекта MSBuild с нуля](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Содержит описание способов пошагового создания основного файла проекта путем использования только текстового редактора.|  
|[Пошаговое руководство. Использование MSBuild](../msbuild/walkthrough-using-msbuild.md)|Содержит вводную информацию о стандартных блоках MSBuild и описание способов записи, управления и отладки проектов MSBuild без выхода из интегрированной среды разработки Visual Studio.|  
|[Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)|Содержит ссылки на документы, содержащие справочную информацию.|  
|[MSBuild](../msbuild/msbuild.md)|Предоставляет общие сведения о схеме XML для файла проекта и показывает способ управления процессами, осуществляющими сборку программного обеспечения.|