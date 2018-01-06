---
title: "Открытие и сохранение элементы проекта | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a270811cc13d4b0e9af027ec2b4b5d2032582a3e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="opening-and-saving-project-items"></a>Открытие и сохранение элементов проекта
При добавлении нового типа проекта, необходимо управлять Открытие и сохранение файлов проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). В следующих разделах рассматриваются различные способы открытия и сохранения файлов.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Отображение файлов с помощью команды "Открыть файл"](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Предоставляет пошаговое объяснение как IDE обрабатывает **открыть файл** команда и роли проектов реагировать на эту команду.  
  
 [Отображение файлов с помощью команды "Открыть с помощью"](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Предоставляет пошаговые объяснение как IDE обрабатывает **открыть с помощью** команды запроса открытия файла, который имеет некоторые Выбор стандартной редакторов.  
  
 [Практическое руководство. Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)  
 Содержит пошаговые инструкции для указания, что файлы определенного типа в проекте должен быть открыт с помощью редактора для конкретного проекта.  
  
 [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)  
 Содержит пошаговые инструкции для указания способа включить интегрированную среду разработки для открытия стандартного редактора для файлов в тип проекта.  
  
 [Практическое руководство. Открытие редакторов для открытых документов](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Предоставляет пошаговые инструкции, чтобы открыть редактор для конкретного проекта для открытого файла.  
  
 [Сохранение стандартного документа](../../extensibility/internals/saving-a-standard-document.md)  
 Содержит подробное описание того, как IDE обрабатывает **Сохранить**, **Сохранить как**, и **сохранить все** команд для документа открывается в стандартном редакторе.  
  
 [Сохранение настраиваемого документа](../../extensibility/internals/saving-a-custom-document.md)  
 Предоставляет схему и подробное описание того, как IDE обрабатывает **Сохранить**, **Сохранить как**, и **сохранить все** команд для документов, открытых в специализированный редактор.  
  
 [Определение редактора, с помощью которого откроется файл в проекте](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 Описывает процесс, который следует за интегрированной среды разработки, можно выбрать соответствующий редактор или конструктор для файла.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание специализированных редакторов и конструкторов](../../extensibility/creating-custom-editors-and-designers.md)  
 Список типов четырех редакторов, интегрированной среды разработки, можно разместить и предоставляет описания каждого редактора отдельно.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Описывает управление способом, что код компилируется и построение проектов, открываются как редакторы и способ форматирования элементов проекта.