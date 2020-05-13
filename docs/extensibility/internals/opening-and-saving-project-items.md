---
title: Элементы проекта по открытию и сохранению (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706970"
---
# <a name="opening-and-saving-project-items"></a>Открытие и сохранение элементов проекта
При добавлении нового типа проекта необходимо управлять открытием и [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сохранением файлов проектов в интегрированной среде разработки (IDE). Ниже обсуждаются различные подходы к открытию и сохранению файлов.

## <a name="in-this-section"></a>В этом разделе
- [Отображение файлов с помощью команды "Открыть файл"](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Предоставляет пошаговый разъяснение того, как IDE обрабатывает команду **Open File,** и роль проектов в ответе на эту команду.

- [Отображение файлов с помощью команды "Открыть с помощью"](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Предоставляет подробное, пошаговое объяснение того, как IDE обрабатывает **команду Open With,** что приводит к открытию файла, который имеет некоторый выбор стандартных редакторов.

- [Практическое руководство. Открытие редакторов соответствующих проектов](../../extensibility/how-to-open-project-specific-editors.md)

 Предоставляет пошаговые инструкции для указания того, что файлы определенного типа в проекте должны быть открыты с помощью редактора, конкретного проекта.

- [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)

 Предоставляет пошаговые инструкции для указания того, как позволить IDE открыть стандартный редактор для файлов в типе проекта.

- [Практическое руководство. Открытие редакторов для открытых документов](../../extensibility/how-to-open-editors-for-open-documents.md)

 Предоставляет пошаговые инструкции по открытию редактора для открытого файла для конкретного проекта.

- [Сохранение стандартного документа](../../extensibility/internals/saving-a-standard-document.md)

 Предоставляет подробное объяснение того, как IDE обрабатывает **Сохранение,** **Сохранить как**, и **сохранить все** команды для документа, открытого в стандартном редакторе.

- [Сохранение настраиваемого документа](../../extensibility/internals/saving-a-custom-document.md)

 Предоставляет диаграмму и подробное объяснение того, как IDE обрабатывает **Сохранение,** **Сохранить как**, и **сохранить все** команды для документов, открытых в пользовательском редакторе.

- [Определение редактора, с помощью которого откроется файл в проекте](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Обсуждает процесс, который следует IDE, чтобы выбрать подходящий редактор или дизайнер для файла.

## <a name="related-sections"></a>Связанные разделы
- [Создание специализированных редакторов и конструкторов](../../extensibility/creating-custom-editors-and-designers.md)

 Перечисляет четыре типа редакторов, которые IDE может размещать, и дает описания каждого редактора.

- [Типы проектов](../../extensibility/internals/project-types.md)

 Обсуждается, как проекты контролируют способ компилирования и построения кода, как открываются редакторы и как отформатируются элементы проекта.
