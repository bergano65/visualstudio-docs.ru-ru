---
title: Отображение файлов при помощи команды "Открыть с помощью" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de43b6c4f441f8c6bde2d6c248274aed3937a7ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842508"
---
# <a name="displaying-files-by-using-the-open-with-command"></a>Отображение файлов с помощью команды "Открыть с помощью"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Проект может попросить интегрированной среды разработки отобразить диалоговое окно " **Открыть с помощью** ". Этот запрос предлагает пользователю открыть файл с выбранными стандартными редакторами. Следующие шаги описывают данный процесс.  
  
1. Проект вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , указывая значение OSE_UseOpenWithDialog для `OSEOpenDocEditor` параметра.  
  
2. На основе расширения имени файла документа интегрированная среда разработки определяет, какие редакторы, перечисленные в реестре, могут открыть указанный документ и отобразить эти сведения в диалоговом окне **Открыть с помощью** .  
  
    > [!NOTE]
    > Проекты, имеющие встроенный редактор, который должен быть добавлен в диалоговое окно « **Открыть с помощью** », должны зарегистрировать фабрику редактора для каждого такого редактора. Встроенные редакторы работают только вместе с определенным типом проекта, который применяется в реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метода. Интегрированная среда разработки имеет встроенную фабрику редактора для основного текстового редактора и двоичного редактора. Интегрированная среда разработки также создает экземпляр фабрики редактора от имени каждой зарегистрированной ассоциации файлов Windows. Примером такого файла является Microsoft Word.  
  
3. Как только пользователь выбирает элемент в диалоговом окне **Открыть с помощью** , интегрированная среда разработки открывает документ путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> метода. Дополнительные сведения см. [в разделе как открыть стандартные редакторы](../../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>См. также:  
 [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Отображение файлов с помощью команды "открыть файл"](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [Практическое руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)
