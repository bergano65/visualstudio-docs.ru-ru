---
title: Открытие и сохранение элементов проекта | Документация Майкрософт
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
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c1013253f39dec2b3d0a97f1bc4b8deb2dca913a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568407"
---
# <a name="opening-and-saving-project-items"></a>Открытие и сохранение элементов проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Открытие и сохранение элементов проекта](https://docs.microsoft.com/visualstudio/extensibility/internals/opening-and-saving-project-items).  
  
Когда вы добавляете новый тип проекта, необходимо управлять открытия и сохранения файлов проектов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среды разработки (IDE). В следующих разделах рассматриваются различные способы открытия и сохранения файлов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Отображение файлов с помощью команды "Открыть файл"](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Предоставляет пошаговое объяснение как среда IDE обрабатывает **открыть файл** команды и роль проекты при реагировании на эту команду.  
  
 [Отображение файлов с помощью команды "Открыть с помощью"](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Содержит пошаговые объяснение как среда IDE обрабатывает **открыть с помощью** команды, открытие файла, который имеет некоторые Выбор стандартные редакторы запросов.  
  
 [Практическое руководство. Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)  
 Содержит пошаговые инструкции для указания, что файлы определенного типа в проекте должен быть открыт с помощью редактора определенного проекта.  
  
 [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)  
 Содержит пошаговые инструкции по указанию Включение интегрированной среды разработки открыть стандартный редактор для файлов в тип проекта.  
  
 [Практическое руководство. Открытие редакторов для открытых документов](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Содержит пошаговые инструкции, чтобы открыть проектного редактора для открытого файла.  
  
 [Сохранение стандартного документа](../../extensibility/internals/saving-a-standard-document.md)  
 Предоставляет подробные сведения о том, как среда IDE обрабатывает **Сохранить**, **Сохранить как**, и **сохранить все** команды для документ открыт в стандартный редактор.  
  
 [Сохранение настраиваемого документа](../../extensibility/internals/saving-a-custom-document.md)  
 Предоставляет схему и подробные сведения о том, как среда IDE обрабатывает **Сохранить**, **Сохранить как**, и **сохранить все** команд для документов, открытых в специализированный редактор.  
  
 [Определение редактора, с помощью которого откроется файл в проекте](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Описание процесса, который следует за интегрированной среды разработки, можно выбрать соответствующий редактор или конструктор для файла.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание специализированных редакторов и конструкторов](../../extensibility/creating-custom-editors-and-designers.md)  
 Список четырех типов редакторов, что можно разместить интегрированной среды разработки и предоставляет описание каждого редактора отдельно.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Описывается, как проекты управлять способом, что код скомпилированы и собраны, способ открытия редакторов и способ форматирования элементов проекта.

