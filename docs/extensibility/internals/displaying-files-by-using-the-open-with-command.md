---
title: Отображение файлов, выполнив команду открытия | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9c708bb5a510748b08cac5b46b6829b908e74e0a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Отображение файлов, выполнив команду открытия
Проект можно попросить IDE, чтобы отобразить **открыть с помощью** диалоговое окно. Этот запрос предлагает пользователю открыть файл, содержащий набор стандартных редакторов. Следующие шаги описывают этот процесс.  
  
1.  Вызовы проекта <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, указав значение OSE_UseOpenWithDialog для `OSEOpenDocEditor` параметра.  
  
2.  Определяет, какие редакторы, перечисленных в реестре могут открыть указанный документ на основании расширение имени файла документа, интегрированной среды разработки и отображает эту информацию в **открыть с помощью** диалоговое окно.  
  
    > [!NOTE]
    >  Проекты, содержащие встроенный редактор, который должен быть включен в **открыть с помощью** диалоговое окно необходимо зарегистрировать фабрику редактора для каждого такого редактора. Встроенная функция редакторы работать вместе с определенного типа проекта, который применяется в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метод. Среда IDE содержит встроенный редактор фабрику для базового редактора текста и двоичный редактор. Также IDE создает экземпляр фабрики редактора от имени каждого зарегистрированного сопоставления файлов Windows. Примером такого файла является Microsoft Word.  
  
3.  Как только пользователь выбирает элемент из **открыть с помощью** документ откроется диалоговое окно, затем IDE путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метод. Дополнительные сведения см. в разделе [как: стандартные редакторы](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>См. также  
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Отображение файлов с помощью команды Открыть файл](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)